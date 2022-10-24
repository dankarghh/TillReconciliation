<script setup>
import { ref, computed } from "vue";
import TillTotal from "./TillTotal.vue";

const dateOfBanking = ref(null);
const dateOfDeposit = ref(null);
const notesTotal = computed(() => {});
const coinTotal = computed(() => {});
const despositBag = ref(null);

const allTills = ref([]);
</script>

<template>
  <TillTotal />
</template>
