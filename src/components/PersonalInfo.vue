<script setup>
import { inject, provide, ref } from "vue";
import Buttons from "./Buttons.vue";
import "../assets/style.css";
const gender = ref("");

const showButtons = inject("showButtons");

if (!showButtons) {
  throw new Error("showButtons was not provided");
}

showButtons.showPrevious = false;
</script>
<template>
  <div class=".form-container">
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
<!-- <style scoped>
.personal-details-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 20px;
  width: 80%;
  background: rgb(237, 246, 247);
  padding: 30px;
}
.personal-details-container h1 {
  color: rgba(77, 204, 132, 0.881);
  font-size: 15px;
}
.personal-details-container form {
  display: flex;
  flex-direction: column;
  width: 70%;
  gap: 30px;
}
.personal-details-container form input,
.personal-details-container form select {
  height: 3rem;
  border: none;
  padding: 0 10px;
}
.personal-details-container form input:focus,
.personal-details-container form select:focus {
  outline: 2px solid rgba(77, 204, 132, 0.881);
}
.personal-details-container form input::placeholder {
  color: black;
}
</style> -->
