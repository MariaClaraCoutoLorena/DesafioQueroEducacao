<script
  lang="ts"
  setup
>
import { defineProps } from 'vue';
import QText from "./QText.vue";
import QBadge from "./QBadge.vue";

defineProps<{
  fullPrice: string;
  offeredPrice: string;
  discount: string;
}>()
</script>

<template>
<div class="flex gap-2 items-end">
  <div class="flex flex-col">
    <QText
      tag="del"
      color="minor"
      size="sm"
    >
      {{ fullPrice }}
    </QText>
    <QText
      tag="ins"
      size="lg"
      weight="semibold"
    >
      {{ offeredPrice }}
    </QText>
  </div>
  <QBadge>
    {{ discount }}
  </QBadge>
</div>
</template>