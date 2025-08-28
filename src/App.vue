<script
  setup
  lang="ts"
>
import { ref } from 'vue';

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

const offers = ref([])
</script>

<template>
<QLayout>
  <template #header>
    <QHeader>
      <QInput
        type="search"
        id="site-search"
        name="q"
        placeholder="Busque o curso ideal para você"
        aria-label="Buscar cursos e bolsas"
      />
      <QButton type="submit">Buscar</QButton>
    </QHeader>
  </template>

  <template #sidebar>
    <QFormFilterOffer />
  </template>

  <QSectionForm title="Veja as opções que encontramos">
    <template #filter>
      <QFormFilterOffer />
    </template>

    <template #order-by>
      <QFormOrderByOffer />
    </template>
  </QSectionForm>

  <QListCard
    :cards="offers"
    class="mt-6"
  >
    <template #default="{ card }">
      <QCardOffer
        :course-name="card.courseName"
        :rating="card.rating"
        :full-price="card.fullPrice"
        :offered-price="card.offeredPrice"
        :discount="card.discount"
        :kind="card.kind"
        :level="card.level"
        :ies-logo="card.iesLogo"
        :ies-name="card.iesName"
      />
    </template>
  </QListCard>

  <template #footer>
    <QFooter />
  </template>
</QLayout>
</template>