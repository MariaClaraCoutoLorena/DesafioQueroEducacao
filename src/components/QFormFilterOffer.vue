<script
  setup
  lang="ts"
>

import QHeading from "./QHeading.vue";
import QInputCheckbox from "./QInputCheckbox.vue";
import QInputRange from "./QInputRange.vue";
import QFieldset from "./QFieldset.vue";
</script>

<template>
<form action="#">
  <QHeading tag="h1">Filtros</QHeading>

  <hr class="my-5">

  <QFieldset legend="Graduação">
    <QInputCheckbox label="Bacharelado" />

    <QInputCheckbox label="Licenciatura" />

    <QInputCheckbox label="Técnologo" />
  </QFieldset>

  <hr class="my-5">

  <QFieldset legend="Modalidade do curso">
    <QInputCheckbox
      label="Presencial"
      :count="87"
    />

    <QInputCheckbox
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
