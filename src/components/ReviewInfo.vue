<script setup>
import Buttons from "./Buttons.vue";
</script>
<template>
  <div class="form-container">
    <h1>Step 3: Review and Submit</h1>
    <form>
      <input type="text" placeholder="First Name" />
      <input type="text" placeholder="Second Name" />
      <input type="date" placeholder="" />
      <select>
        <option disabled value="" class="disabled">Gender</option>
        <option value="male">Male</option>
        <option value="female">Female</option>
        <option value="not_specify">Not specify</option>
      </select>
      <input type="text" placeholder="Your Email" />
      <input type="password" placeholder="Your Password" />
      <input type="password" placeholder="Confirm Password" />
      <button type="submit" class="submit-btn">Submit</button>
    </form>
    <Buttons />
  </div>
</template>
