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
    <QIconStar />
    <QIconStar />
    <QIconStar />
    <QIconStar />
    <QIconStar half />
  </div>
</div>
</template>