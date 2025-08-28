<script
  setup
  lang="ts"
>
import { defineProps, defineEmits, Transition } from 'vue';

defineProps<{
  open: boolean,
}>();

defineEmits(['closed']);
</script>

<template>
<Transition
  enter-active-class="transition-opacity ease duration-300"
  enter-from-class="opacity-0"
  leave-active-class="transition-opacity ease duration-300"
  leave-to-class="opacity-0"
>
  <div
    v-if="open"
    class="fixed inset-0 bg-black bg-opacity-50"
    @click="$emit('closed')"
  />
</Transition>

<Transition
  enter-active-class="transform transition-transform ease duration-300"
  enter-from-class="translate-y-full"
  leave-active-class="transform transition-transform ease duration-300"
  leave-to-class="translate-y-full"
>
  <div
    v-if="open"
    class="fixed inset-x-0 bottom-0 bg-white p-4 rounded-t-xl shadow-lg max-w-lg mx-auto"
    @click.stop
  >
    <slot></slot>
  </div>
</Transition>
</template>