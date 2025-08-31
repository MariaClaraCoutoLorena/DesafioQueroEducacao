<script
  setup
  lang="ts"
>

  import QInputRadio from "./QInputRadio.vue";
  import QHeading from "./QHeading.vue";

  defineProps<{
    modelValue: string;
  }>()

  const emit = defineEmits<{
    (e: 'update:modelValue', value: string): void;
  }>()

</script>

<template>
  <form action="#">
    <QHeading
      tag="h2"
      size="sm"
      class="mb-2"
    >
      Ordenar
    </QHeading>

    <QInputRadio
      label="Cursos de A-Z"
      name="order-by"
      value="course-name"
      :checked="modelValue === 'course-name'"
      @change="emit('update:modelValue', 'course-name')"
    />

    <QInputRadio
      label="Menor preço"
      name="order-by"
      value="price"
      :checked="modelValue === 'price'"
      @change="emit('update:modelValue', 'price')"
    />

    <QInputRadio
      label="Melhor avaliados"
      name="order-by"
      value="rating"
      :checked="modelValue === 'rating'"
      @change="emit('update:modelValue', 'rating')"
    />
  </form>
</template>
