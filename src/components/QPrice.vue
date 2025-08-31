<script
  lang="ts"
  setup
>
  import { defineProps } from 'vue';
  import QText from "./QText.vue";
  import QBadge from "./QBadge.vue";

  defineProps<{
    fullPrice: number;
    offeredPrice: number ;
    discount: number;
  }>()

  function formatPrice(price: number): string {
    return new Intl.NumberFormat('pt-BR', { style: 'currency', currency: 'BRL' }).format(price);
  }


</script>

<template>
<div class="flex gap-2 items-end">
  <div class="flex flex-col">
    <QText
      tag="del"
      color="minor"
      size="sm"
    >
      {{ formatPrice(fullPrice) }}
    </QText>
    <QText
      tag="ins"
      size="lg"
      weight="semibold"
    >
      {{ formatPrice(offeredPrice) }}
    </QText>
  </div>
  <QBadge>
    {{ `- ${(discount*100).toFixed(0)}%` }}
  </QBadge>
</div>
</template>