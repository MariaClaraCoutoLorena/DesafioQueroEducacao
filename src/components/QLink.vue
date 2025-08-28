<script
  lang="ts"
  setup
>
import { useAttrs, defineProps, withDefaults } from 'vue';

withDefaults(defineProps<{
  size?: 'xs' | 'sm' | 'md' | 'lg';
}>(), {
  size: 'md',
});

const attrs = useAttrs();
</script>

<template>
<a
  v-bind="attrs"
  class="text-primary-pure hover:text-primary-darkest hover:underline"
  :class="[
    {
      'xs': 'text-xs',
      'sm': 'text-sm',
      'md': 'text-base',
      'lg': 'text-lg',
    }[size],
  ]"
>
  <slot />
</a>
</template>