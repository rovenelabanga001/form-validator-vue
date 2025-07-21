<script setup>
import { provide, reactive, ref } from "vue";
import PersonalInfo from "./PersonalInfo.vue";
import AccountSetup from "./AccountSetup.vue";
import "../assets/style.css";
import ReviewInfo from "./ReviewInfo.vue";
import ProgressBar from "./ProgressBar.vue";

const formData = reactive({
  firstName: "",
  secondName: "",
  dateOfBirth: "",
  gender: "",
  email: "",
  password: "",
  confirmPassword: "",
});
const currentStep = ref(0);
const stepCount = 3;

const nextStep = () => {
  if (currentStep.value < stepCount - 1) {
    currentStep.value++;
  }
};

const prevStep = () => {
  if (currentStep.value > 0) {
    currentStep.value--;
  }
};

provide("currentStep", currentStep);
provide("nextStep", nextStep);
provide("prevStep", prevStep);
</script>

<template>
  <div class="app-container">
    <h1>User Registration</h1>
    <!-- using is to dynamically bind a value to the components -->
    <ProgressBar :stepCount="stepCount" />
    <component :is="[PersonalInfo, AccountSetup, ReviewInfo][currentStep]" :formData="formData" />
  </div>
</template>
<style scoped>
.app-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 3rem 15rem;
  gap: 20px;
}
.app-container h1 {
  color: rgba(77, 204, 132, 0.881);
  font-size: 20px;
}
</style>
