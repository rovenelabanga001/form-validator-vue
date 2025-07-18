<script setup>
import { inject, provide, ref } from "vue";
import Buttons from "./Buttons.vue";
const gender = ref("");

const showButtons = inject("showButtons");

if (!showButtons) {
  throw new Error("showButtons was not provided");
}
</script>
<template>
  <div class="form-container pesonal-details">
    <h1>Personal Details</h1>
    <form>
      <input type="text" placeholder="First Name" />
      <input type="text" placeholder="Second Name" />
      <input type="date" placeholder="" />
      <select v-model="gender">
        <option disabled value="" class="disabled">Gender</option>
        <option value="male">Male</option>
        <option value="female">Female</option>
        <option value="not_specify">Not specify</option>
      </select>
    </form>
    <Buttons />
  </div>
</template>
