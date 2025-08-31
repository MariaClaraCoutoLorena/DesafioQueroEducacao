<script
  setup
  lang="ts"
>
  import { ref, onMounted, computed } from 'vue';

  import QHeader from "./components/QHeader.vue";
  import QInput from "./components/QInput.vue";
  import QButton from "./components/QButton.vue";
  import QCardOffer from "./components/QCardOffer.vue";
  import QFooter from "./components/QFooter.vue";
  import QLayout from "./components/QLayout.vue";
  import QListCard from "./components/QListCard.vue";
  import QSectionForm from "./components/QSectionForm.vue";
  import QFormOrderByOffer from "./components/QFormOrderByOffer.vue";
  import QFormFilterOffer from "./components/QFormFilterOffer.vue";

  interface Offer {
    id: string;
    courseName: string;
    rating: number;
    fullPrice: string;
    offeredPrice: string;
    kind: string;
    level: string;
    iesLogo: string;
    iesName: string;
  }
  const order = ref('course-name');
  const offers = ref<Offer[]>([]);
  const isLoading = ref(true);
  const error = ref<string | null>(null);
  const searchInput = ref('');
  const searchQuery = ref('');

  function applySearch() {
    searchQuery.value = searchInput.value;
  }

  onMounted(async () => {
    try {
      const response = await fetch('http://localhost:3000/offers');

      if (!response.ok) {
        throw new Error('Falha ao acessar o servidor!');
      }
      const data = await response.json();
      offers.value = data

    } catch (e: any) {
      error.value = e.message || 'Ocorreu um erro inesperado.';
    } finally {
      isLoading.value = false;
    }
  });

  const sortedFilterOffers = computed(() => {
    let offersCopy = [...offers.value];

    if (searchQuery.value !== '') {
      const query = searchQuery.value.normalize("NFD").replace(/[\u0300-\u036f]/g, "").toLowerCase();
      offersCopy = offersCopy.filter(offer => offer.courseName.normalize("NFD").replace(/[\u0300-\u036f]/g, "").toLowerCase().includes(query));
    }

    switch (order.value) {
      case 'course-name':
        return offersCopy.sort((a, b) => a.courseName.localeCompare(b.courseName));
      
      case 'price':
        return offersCopy.sort((a, b) => parseFloat(a.offeredPrice) - parseFloat(b.offeredPrice));
        
      case 'rating':
        return offersCopy.sort((a, b) => b.rating - a.rating);
        
      default:
        return offersCopy;
    }
  });

 




</script>

<template>
  <QLayout>

    <template #header>
      <QHeader>
        <form @submit.prevent="applySearch" class="flex w-full">
          <QInput
            v-model="searchInput"
            type="search"
            id="site-search"
            name="q"
            placeholder="Busque o curso ideal para você"
            aria-label="Buscar cursos e bolsas"
          />
          <QButton type="submit">Buscar</QButton>
        </form>
        
      </QHeader>
    </template>

    <template #sidebar>
      <QFormFilterOffer />
    </template>

    <template #main-content>

      <QSectionForm title="Veja as opções que encontramos">
        <template #filter>
          <QFormFilterOffer />
        </template>

        <template #order-by>
          <QFormOrderByOffer v-model="order"/>
        </template>
      </QSectionForm>

      <QListCard :cards="sortedFilterOffers" class="mt-6">
        <template #default="{ card }">
          <QCardOffer
            :course-name="card.courseName"
            :rating="card.rating"
            :full-price="parseFloat(card.fullPrice)"
            :offered-price="parseFloat(card.offeredPrice)"
            :discount="card.fullPrice && card.offeredPrice ? ( 1 - parseFloat(card.offeredPrice)/parseFloat(card.fullPrice)) : 0"
            :kind="card.kind"
            :level="card.level"
            :ies-logo="card.iesLogo"
            :ies-name="card.iesName"
          />
        </template>
      </QListCard>

    </template>

    

    

    <template #footer>
      <QFooter />
    </template>

  </QLayout>
</template>