<script
  lang="ts"
  setup
>
import { defineProps } from 'vue';
import QIconStar from "./QIconStar.vue";
import QText from "./QText.vue";

defineProps<{
  rating: number;
}>()
</script>

<template>
<div class="flex items-center gap-2">
  <QText tag="span">
    {{ rating }}
  </QText>
  <div class="flex items-center space-x-1 text-yellow-500">
    <QIconStar
      v-for="n in Math.floor(rating)"
      :key="n"
    />
    <QIconStar half 
      v-if=" rating - Math.floor(rating) > 0"
    />
  </div>
</div>
</template>