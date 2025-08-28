<script
  setup
  lang="ts"
>

import QInputRadio from "./QInputRadio.vue";
import QHeading from "./QHeading.vue";
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
    checked
  />

  <QInputRadio
    label="Menor preço"
    name="order-by"
    value="price"
  />

  <QInputRadio
    label="Melhor avaliados"
    name="order-by"
    value="rating"
  />
</form>
</template>
