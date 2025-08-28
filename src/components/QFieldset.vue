<script
  setup
  lang="ts"
>
import { defineProps } from 'vue'
import QText from "./QText.vue";

defineProps<{
  legend: string;
}>()
</script>

<template>
<fieldset>
  <QText
    tag="legend"
    size="sm"
    weight="medium"
    class="mb-3"
  >
    {{ legend }}
  </QText>
  <slot />
</fieldset>
</template>
