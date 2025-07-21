<script setup>
import { inject, toRefs } from "vue";
import Buttons from "./Buttons.vue";
import { toast } from "vue3-toastify";
import "vue3-toastify/dist/index.css";

const props = defineProps(["formData"]);
const emit = defineEmits(["validated", "resetAll"]);
const { isValidEmail, checkPasswords } = inject("validators");

const { firstName, secondName, dateOfBirth, gender, email, password, confirmPassword } = toRefs(
  props.formData
);

const validateForm = () => {
  if (
    !firstName.value ||
    !secondName.value ||
    !dateOfBirth.value ||
    !gender.value ||
    !email.value ||
    !password.value ||
    !confirmPassword.value
  ) {
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
  if (validateForm()) {
    toast.success("User created successfully");
    setTimeout(() => emit("resetAll"), 3000);
  }
};
</script>
<template>
  <div class="form-container">
    <h1>Step 3: Review and Submit</h1>
    <form @submit.prevent="handleSubmit">
      <input type="text" placeholder="First Name" v-model="firstName" />
      <input type="text" placeholder="Second Name" v-model="secondName" />
      <input type="date" placeholder="" v-model="dateOfBirth" />
      <select v-model="gender">
        <option disabled value="" class="disabled">Gender</option>
        <option value="male">Male</option>
        <option value="female">Female</option>
        <option value="not_specify">Not specify</option>
      </select>
      <input type="text" placeholder="Your Email" v-model="email" />
      <input type="password" placeholder="Your Password" v-model="password" />
      <input type="password" placeholder="Confirm Password" v-model="confirmPassword" />
      <button type="submit" class="submit-btn">Submit</button>
    </form>
    <Buttons />
  </div>
</template>
