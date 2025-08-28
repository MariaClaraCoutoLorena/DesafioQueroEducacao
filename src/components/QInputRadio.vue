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
<label class="flex items-center text-sm py-2 justify-items-start cursor-pointer">
  <input
    v-bind="attrs"
    type="radio"
  />
  <QText
    tag="span"
    weight="light"
    class="ml-2"
  >
    {{ label }}
  </QText>
</label>
</template>