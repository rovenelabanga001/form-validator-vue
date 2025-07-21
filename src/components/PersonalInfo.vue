<script setup>
import { computed, toRefs } from "vue";
import Buttons from "./Buttons.vue";
import { toast } from "vue3-toastify";
import "vue3-toastify/dist/index.css";

const today = computed(() => {
  const now = new Date();
  return now.toISOString().split("T")[0];
});

const props = defineProps(["formData"]);
const emit = defineEmits(["validated"]);
const { firstName, secondName, dateOfBirth, gender } = toRefs(props.formData);

const validateForm = () => {
  if (!firstName.value || !secondName.value || !dateOfBirth.value || !gender.value) {
    toast.error("Please fill all required fields");
    return false;
  }
  return true;
};

const handleSubmit = () => {
  const isValid = validateForm();
  emit("validated", isValid);
  console.log(props.formData);
};
</script>
<template>
  <div class="form-container pesonal-details">
    <h1>Step 1: Personal Details</h1>
    <form @submit.prevent="handleSubmit">
      <input type="text" placeholder="First Name" v-model="firstName" />
      <input type="text" placeholder="Second Name" v-model="secondName" />
      <input type="date" placeholder="" :max="today" v-model="dateOfBirth" />
      <select v-model="gender">
        <option disabled value="" class="disabled">Gender</option>
        <option value="male">Male</option>
        <option value="female">Female</option>
        <option value="not_specify">Not specify</option>
      </select>
      <button type="submit" class="submit-btn">Submit</button>
    </form>
    <Buttons @triggerValidation="handleSubmit" />
  </div>
</template>
