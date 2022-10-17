<script setup>
import { ref, computed } from "vue";
import TillTotal from "./TillTotal.vue";

const dateOfBanking = ref(null);
const dateOfDeposit = ref(null);
const notesTotal = computed(() => {});
const coinTotal = computed(() => {});
const despositBag = ref(null);
</script>

<template>
  <TillTotal />
</template>
