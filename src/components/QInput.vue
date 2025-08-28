<script
  lang="ts"
  setup
>
import { useAttrs } from 'vue';

const attrs = useAttrs();
</script>

<template>
<input
  v-bind="attrs"
  class="border border-zinc-300 w-full p-3 text-sm rounded-lg"
/>
</template>