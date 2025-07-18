<script setup>
import { inject } from "vue";

const currentStep = inject("currentStep");
const nextStep = inject("nextStep");
const prevStep = inject("prevStep");
</script>
<template>
  <div class="buttons-container">
    <button v-if="currentStep > 0" @click="prevStep">Previous</button>
    <button v-if="currentStep < 2" @click="nextStep">Next</button>
  </div>
</template>
<style scoped>
.buttons-container {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  width: 70%;
  padding: 20px;
}
.buttons-container button {
  background: rgba(77, 204, 132, 0.881);
  color: white;
  border: none;
  cursor: pointer;
  height: 2rem;
  width: 4rem;
  transition: 0.5s;
}

.buttons-container button:hover {
  background: white;
  color: rgba(77, 204, 132, 0.881);
}
</style>
