<script setup>
import { inject, provide, ref } from "vue";
import Buttons from "./Buttons.vue";

const props = defineProps(["formData"]);

const handleSubmit = () => {
  console.log(props.formData);
};
</script>
<template>
  <div class="form-container pesonal-details">
    <h1>Step 1: Personal Details</h1>
    <form @submit.prevent="handleSubmit">
      <input type="text" placeholder="First Name" v-model="formData.firstName" />
      <input type="text" placeholder="Second Name" v-model="formData.secondName" />
      <input type="date" placeholder="" v-model="formData.date" />
      <select v-model="formData.gender">
        <option disabled value="" class="disabled">Gender</option>
        <option value="male">Male</option>
        <option value="female">Female</option>
        <option value="not_specify">Not specify</option>
      </select>
      <button type="submit" class="submit-btn">Submit</button>
    </form>
    <Buttons />
  </div>
</template>
