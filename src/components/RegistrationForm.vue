<script setup>
import { provide, reactive, ref } from "vue";
import PersonalInfo from "./PersonalInfo.vue";
import AccountSetup from "./AccountSetup.vue";
import "../assets/style.css";
import ReviewInfo from "./ReviewInfo.vue";
import ProgressBar from "./ProgressBar.vue";
import { toast } from "vue3-toastify";
import "vue3-toastify/dist/index.css";

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

const checkPasswords = (password, confirmPassword) => {
  if (password !== confirmPassword) {
    toast.error("Passwords must match");
    return false;
  }
  return true;
};

const isValidEmail = (email) => {
  const regex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
  return regex.test(email);
};

provide("currentStep", currentStep);
provide("nextStep", nextStep);
provide("prevStep", prevStep);
provide("validators", { isValidEmail, checkPasswords });

const handleValidation = (isValid) => {
  if (isValid) {
    nextStep();
  }
};

const resetAll = () => {
  const resetFormData = () => {
    formData.firstName = "";
    formData.secondName = "";
    formData.dateOfBirth = "";
    formData.gender = "";
    formData.email = "";
    formData.password = "";
    formData.confirmPassword = "";
  };

  resetFormData();

  currentStep.value = 0;
};
</script>

<template>
  <div class="app-container">
    <h1>User Registration</h1>
    <ProgressBar :stepCount="stepCount" />
    <!-- using is to dynamically bind a value to the components -->
    <component
      :is="[PersonalInfo, AccountSetup, ReviewInfo][currentStep]"
      :formData="formData"
      @validated="handleValidation"
      @resetAll="resetAll"
    />
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
