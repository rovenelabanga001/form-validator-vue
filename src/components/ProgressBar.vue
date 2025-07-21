<script setup>
import { inject } from "vue";

const currentStep = inject("currentStep");
const nextStep = inject("nextStep");
const prevStep = inject("prevStep");

const props = defineProps(["stepCount"]);
</script>
<template>
  <div class="progress-wrapper">
    <div class="progress-bar" :style="{ width: ((currentStep + 1) / stepCount) * 100 + '%' }"></div>
  </div>
</template>

<style scoped>
.progress-wrapper {
  width: 100%;
  height: 8px;
  background-color: #e0e0e0;
  border-radius: 4px;
  margin-bottom: 20px;
  overflow: hidden;
}
.progress-bar {
  height: 100%;
  background-color: #4dcf84;
  width: 0%;
  transition: width 0.3s ease-in-out;
}
</style>
