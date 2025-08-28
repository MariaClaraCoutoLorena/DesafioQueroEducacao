<script
  setup
  lang="ts"
>
import { ref, onMounted, onBeforeUnmount } from 'vue'

const isPopoverOpen = ref(false)
const popover = ref<HTMLElement | null>(null)

const openPopover = () => {
  setTimeout(() => {
    isPopoverOpen.value = true
  })
}

const handleClickOutside = (event: MouseEvent) => {
  if (popover.value && !popover.value.contains(event.target as Node)) {
    isPopoverOpen.value = false
  }
}

onMounted(() => {
  document.addEventListener('click', handleClickOutside)
})

onBeforeUnmount(() => {
  document.removeEventListener('click', handleClickOutside)
})
</script>

<template>
<div class="relative inline-block">
  <slot
    name="trigger"
    :open="openPopover"
  ></slot>

  <div
    v-show="isPopoverOpen"
    ref="popover"
    class="absolute left-0 transform -translate-x-[70%] mt-3 w-64 bg-white border rounded shadow-lg"
  >
    <div class="p-4">
      <slot name="panel" />
    </div>
  </div>
</div>
</template>
