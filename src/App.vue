<script setup>
import { ref, computed } from "vue";
import Input from "./components/Input.vue";
import TillTotal from "./components/TillTotal.vue";
import SectionCard from "./components/SectionCard.vue";
import DailyBanking from "./components/DailyBanking.vue";
</script>

<template>
  <div class="bg-slate-50">
    <div class="bg-red-500 h-32 m-4 rounded-xl box-content">
      <h1 class="text-white m-4">Welcome to banking</h1>
    </div>
    <DailyBanking />
  </div>
</template>
