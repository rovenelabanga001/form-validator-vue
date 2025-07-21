<script setup>
import { inject } from "vue";
import Buttons from "./Buttons.vue";

const showButtons = inject("showButtons");

if (!showButtons) {
  throw new Error("showButtons was not provided");
}
</script>

<template>
  <div class="form-container">
    <h1>Step 2: Account Setup</h1>
    <form>
      <input type="text" placeholder="Your Email" />
      <input type="password" placeholder="Your Password" />
      <input type="password" placeholder="Confirm Password" />
      <button type="submit" class="submit-btn">Submit</button>
    </form>
    <Buttons />
  </div>
</template>
