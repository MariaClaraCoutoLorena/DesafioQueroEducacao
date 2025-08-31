<script
  setup
  lang="ts"
>
import QRow from "./QRow.vue";
</script>

<template>
  <div class="min-h-screen flex flex-col">
    <div class="border-b">
      <header class="max-w-screen-2xl mx-auto w-full">
        <slot name="header"></slot>
      </header>
    </div>

    <div class="max-w-screen-2xl mx-auto w-full flex-1">
      <QRow class="flex">
        <template #sidebar>
          <aside class="w-[220px] pr-8 border-r py-6 h-full hidden lg:block">
            <slot name="sidebar"></slot>
          </aside>
        </template>

        <main class="py-6">
          <slot name="main-content"></slot>
        </main>
      </QRow>
    </div>

    <footer class="border-t">
      <slot name="footer"></slot>
    </footer>
  </div>
</template>