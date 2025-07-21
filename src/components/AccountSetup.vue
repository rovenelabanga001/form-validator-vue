<script setup>
import { inject, toRefs } from "vue";
import Buttons from "./Buttons.vue";
import { toast } from "vue3-toastify";
import "vue3-toastify/dist/index.css";

const props = defineProps(["formData"]);
const emit = defineEmits(["validated"]);
const { isValidEmail, checkPasswords } = inject("validators");

const { email, password, confirmPassword } = toRefs(props.formData);

const validateForm = () => {
  if (!email.value || !password.value || !confirmPassword.value) {
    toast.error("Please fill all required fields");
    return false;
  }
  if (!isValidEmail(email.value)) {
    toast.error("Please enter a valid email");
    return false;
  }
  if (!checkPasswords(password.value, confirmPassword.value)) {
    return;
  }
  return true;
};

const handleSubmit = () => {
  const isValid = validateForm() && checkPasswords();
  emit("validated", isValid);
  console.log(props.formData);
};
</script>

<template>
  <div class="form-container">
    <h1>Step 2: Account Setup</h1>
    <form @submit.prevent="handleSubmit">
      <input type="text" placeholder="Your Email" v-model="email" />
      <input type="password" placeholder="Your Password" v-model="password" />
      <input type="password" placeholder="Confirm Password" v-model="confirmPassword" />
      <button type="submit" class="submit-btn">Submit</button>
    </form>
    <Buttons />
  </div>
</template>
