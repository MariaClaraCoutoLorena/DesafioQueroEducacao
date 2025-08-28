<script
  setup
  lang="ts"
>
import { ref } from 'vue';
import QRow from "./QRow.vue";
import QButton from "./QButton.vue";
import QIconSearch from "./QIconSearch.vue";
import QBottomSheet from "./QBottomSheet.vue";

const openSearch = ref(false);
</script>

<template>
<section class="h-20 bg-white lg:flex items-center justify-between hidden">
  <QRow>
    <template #sidebar>
      <figure class="flex items-center h-full">
        <img
          src="https://kong.quero.com/logotype-querobolsa.svg"
          alt="Quero Bolsa"
          height="28px"
          width="181px"
        />
      </figure>
    </template>

    <div class="flex gap-4 items-center">
      <slot />
    </div>
  </QRow>
</section>

<section class="flex lg:hidden h-20 bg-white">
  <QRow>
    <div class="flex justify-between h-full items-center">
      <figure class="flex items-center h-full">
        <img
          src="https://kong.quero.com/logotype-querobolsa.svg"
          alt="Quero Bolsa"
          height="28px"
          width="181px"
        />
      </figure>

      <QButton
        variant="secondary"
        @click="openSearch = true"
      >
        <QIconSearch />
      </QButton>
    </div>
  </QRow>
</section>

<QBottomSheet
  :open="openSearch"
  @closed="openSearch = false"
>
  <div class="flex gap-2 flex-col">
    <slot />
  </div>
</QBottomSheet>
</template>
