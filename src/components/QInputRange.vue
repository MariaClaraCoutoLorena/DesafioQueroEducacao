<script
  lang="ts"
  setup
>
  import { defineProps, useAttrs } from 'vue';
  import QText from "./QText.vue";

  defineProps<{
    label: string;
    modelValue: number;
    minValue: number;
    maxValue: number;
  }>();

  const emit = defineEmits<{
    (e: 'update:modelValue', value: number): void;
  }>();

  function handleChange(event: Event) {
    const target = event.target as HTMLInputElement;
    emit('update:modelValue', parseFloat(target.value));
  }

  const attrs = useAttrs();
</script>

<template>
  <QText
    tag="label"
    weight="light"
  >
   Até {{ label }}
  </QText>
  <input
    v-bind="attrs"
    type="range"
    :min="minValue"      
    :max="maxValue"
    :value="modelValue"  
    @input="handleChange"
    class="w-full mt-3 cursor-col-resize"
  />
</template>