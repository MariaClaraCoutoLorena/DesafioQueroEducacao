<script
  setup
  lang="ts"
>
import { defineProps, ref } from 'vue';
import QHeading from "./QHeading.vue";
import QIconBarsArrowUp from "./QIconBarsArrowUp.vue";
import QPopover from "./QPopover.vue";
import QButton from "./QButton.vue";
import QBottomSheet from "./QBottomSheet.vue";

defineProps<{
  title: string;
}>();

const openOrderBy = ref(false);
const openFilter = ref(false);
</script>

<template>
<section class="justify-between items-center hidden lg:flex">
  <QHeading tag="h1">{{ title }}</QHeading>

  <QPopover>
    <template #trigger="{ open }">
      <QButton
        variant="secondary"
        size="sm"
        type="button"
        @click="open"
      >
        <QIconBarsArrowUp />
        Ordenar
      </QButton>
    </template>

    <template #panel>
      <slot name="order-by" />
    </template>
  </QPopover>
</section>

<section class="flex lg:hidden flex-col">
<QHeading tag="h1">{{ title }}</QHeading>

  <div class="flex gap-2 mt-6">
    <QButton
      class="grow"
      size="sm"
      @click="openFilter = true"
    >
      Filtrar
    </QButton>

    <QButton
      class="grow"
      size="sm"
      variant="secondary"
      @click="openOrderBy = true"
    >
      Ordenar
    </QButton>
  </div>
</section>

<QBottomSheet :open="openOrderBy" @closed="openOrderBy = false">
  <slot name="order-by" />
</QBottomSheet>

<QBottomSheet :open="openFilter" @closed="openFilter = false">
  <slot name="filter" />
</QBottomSheet>
</template>