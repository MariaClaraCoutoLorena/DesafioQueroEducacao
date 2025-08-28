<script
  lang="ts"
  setup
>
import { useAttrs, defineProps, withDefaults } from 'vue';

withDefaults(defineProps<{
  tag: keyof HTMLElementTagNameMap;
  size?: 'xs' | 'sm' | 'md' | 'lg';
  weight?: 'light' | 'normal' | 'medium' | 'semibold';
  color?: 'major' | 'minor';
}>(), {
  size: 'md',
  weight: 'normal',
  color: 'major',
});

const attrs = useAttrs();
</script>

<template>
<component
  v-bind="attrs"
  :is="tag"
  :class="[
    {
      'xs': 'text-xs',
      'sm': 'text-sm',
      'md': 'text-base',
      'lg': 'text-lg',
    }[size],
    {
      'light': 'font-light',
      'normal': 'font-normal',
      'medium': 'font-medium',
      'semibold': 'font-semibold',
    }[weight],
    {
      'major': 'text-zinc-950',
      'minor': 'text-zinc-400',
    }[color],
  ]"
>
  <slot />
</component>
</template>