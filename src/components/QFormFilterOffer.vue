<script
  setup
  lang="ts"
>
  import { defineProps, watch } from 'vue';
  import QHeading from "./QHeading.vue";
  import QInputCheckbox from "./QInputCheckbox.vue";
  import QInputRange from "./QInputRange.vue";
  import QFieldset from "./QFieldset.vue";

  const props = defineProps<{
    modelValue: {
      level: string[];
      kind: string[];
      maxPrice: number | null;
    };
    minValue: number;
    maxValue: number;
  }>();
  const emit = defineEmits<{
    (e: 'update:modelValue', value: typeof props.modelValue): void;
  }>();

  watch(() => props.modelValue, (newValue) => {
    emit('update:modelValue', newValue);
  }, { deep: true });

</script>

<template>
<form action="#">
  <QHeading tag="h1">Filtros</QHeading>

  <hr class="my-5">

  <QFieldset legend="Graduação">
    <QInputCheckbox v-model="modelValue.level" value="bacharelado" label="Bacharelado" />

    <QInputCheckbox v-model="modelValue.level" value="licenciatura" label="Licenciatura" />

    <QInputCheckbox v-model="modelValue.level" value="tecnologo" label="Técnologo" />
  </QFieldset>

  <hr class="my-5">

  <QFieldset legend="Modalidade do curso">
    <QInputCheckbox
      v-model="modelValue.kind" value="presencial"
      label="Presencial"
      :count="87"
    />

    <QInputCheckbox
    v-model="modelValue.kind" value="ead"
      label="A distância - EaD"
      :count="24"
    />
  </QFieldset>

  <hr class="my-5">

  <QFieldset legend="Preço da mensalidade">
    <QInputRange label="R$ 340,00" />
  </QFieldset>

  <hr class="mt-5">
</form>
</template>
