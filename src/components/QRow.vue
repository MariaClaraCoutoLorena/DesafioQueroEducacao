<template>
<div class="w-full px-4 lg:px-8">
  <div>
    <slot name="sidebar" />
  </div>
  <div class="pl-0 lg:pl-8 flex-1">
    <slot />
  </div>
</div>
</template>