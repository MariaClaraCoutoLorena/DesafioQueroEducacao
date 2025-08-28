<script
  lang="ts"
  setup
>
import { defineProps, useAttrs } from 'vue';
import QText from "./QText.vue";

defineProps<{
  label: string;
}>();

const attrs = useAttrs();
</script>

<template>
<QText
  tag="label"
  weight="light"
>
  {{ label }}
</QText>
<input
  v-bind="attrs"
  type="range"
  class="w-full mt-3 cursor-col-resize"
/>
</template>