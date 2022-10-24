<script setup>
const props = defineProps({
  title: {
    type: String,
  },
});
</script>

<template>
  <div class="m-4 rounded-xl bg-white shadow-lg overflow-hidden">
    <div class="p-4">
      <slot name="header">{{ title }}</slot>
    </div>
    <div class="p-4">
      <slot name="default"></slot>
    </div>
    <div class="flex justify-end bg-slate-100 p-4 overflow-hidden">
      <slot name="footer"></slot>
    </div>
  </div>
</template>
