<script
  lang="ts"
  generic="Card extends { id: string }"
  setup
>
import { defineProps } from 'vue';

defineProps<{
  cards: Card[];
}>();
</script>

<template>
<ul class="grid gap-4 grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 2xl:grid-cols-5">
  <li
    v-for="card in cards"
    :key="card.id"
  >
    <slot :card="card" />
  </li>
</ul>
</template>