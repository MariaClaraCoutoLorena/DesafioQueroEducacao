<script
  lang="ts"
  setup
>
import { defineProps } from 'vue';
import QText from "./QText.vue";

defineProps<{
  label: string;
}>();
</script>

<template>
<label class="flex items-center text-sm py-2 justify-items-start cursor-pointer">
  <input
    type="checkbox"
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