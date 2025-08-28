<script
  setup
  lang="ts"
>
import QLink from "./QLink.vue";
import QText from "./QText.vue";
</script>

<template>
<section class="bg-gray-50 py-8">
  <div class="container mx-auto flex items-center gap-2 flex-col justify-center text-center">
    <section class="flex gap-2">
      <QText
        size="sm"
        tag="p"
        weight="light"
      >
        Precisa de uma ajuda?
      </QText>
      <QLink
        href="#"
        size="sm"
      >
        Fale conosco
      </QLink>
    </section>
    <section>
      <QText
        tag="small"
        color="minor"
        size="sm"
      >
        &copy; {{ new Date().getFullYear() }} Quero Bolsa • CNPJ
        <data value="10542212000154">10.542.212/0001-54</data>
      </QText>
    </section>
  </div>
</section>
</template>
