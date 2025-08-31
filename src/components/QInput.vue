<script
  lang="ts"
  setup
  >
  import { useAttrs } from 'vue';
  const attrs = useAttrs();

  defineProps<{
    modelValue: string;
  }>();
  const emit = defineEmits<{
    (e: 'update:modelValue', value: string): void;
  }>();
</script>

<template>
<input
  :value="modelValue"
  @input="emit('update:modelValue', ($event.target as HTMLInputElement).value)"
  v-bind="attrs"
  class="border border-zinc-300 w-full p-3 text-sm rounded-lg"
/>
</template>