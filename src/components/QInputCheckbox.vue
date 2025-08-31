<script
  lang="ts"
  setup
>
  import { defineProps, computed } from 'vue';
  import QText from "./QText.vue";

  const props = defineProps<{
    label: string;
    modelValue: string[];
    value: string;
  }>();

  const emit = defineEmits<{
    (e: 'update:modelValue', value: string[]): void;
  }>();

  const isChecked = computed(() => {
    return props.modelValue.includes(props.value);
  });

  function handleChange(event: Event) {
    const target = event.target as HTMLInputElement;
    const newModelValue = [...props.modelValue];

    if (target.checked && !newModelValue.includes(props.value)) {
      newModelValue.push(props.value);
    } else if (!target.checked && newModelValue.includes(props.value)) {
      const index = newModelValue.indexOf(props.value);
      newModelValue.splice(index, 1);
    }
    emit('update:modelValue', newModelValue);
  }
</script>

<template>
<label class="flex items-center text-sm py-2 justify-items-start cursor-pointer">
  <input
    type="checkbox"
    :checked="isChecked"
    @change="handleChange"
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