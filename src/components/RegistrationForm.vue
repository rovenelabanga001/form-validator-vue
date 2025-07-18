<script setup lang="ts">
import { provide, reactive } from "vue";
import PersonalInfo from "./PersonalInfo.vue";


const showButtons = reactive({
  showPrevious: true,
  showNext: true,
});

provide("showButtons", showButtons);
</script>

<template>
  <div class="app-container">
    <h1>User Registration</h1>
    <PersonalInfo />
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
