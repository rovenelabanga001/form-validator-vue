<script setup>
import { inject, toRefs } from "vue";

const injectedButtons = inject("showButtons");

if (!injectedButtons) {
  throw new Error("showButtons was not provided");
}

const { showPrevious, showNext } = toRefs(injectedButtons);
</script>
<template>
  <div class="buttons-container">
    <button v-if="showPrevious">Previous</button>
    <button v-if="showNext">Next</button>
  </div>
</template>
<style scoped>
.buttons-container {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  width: 70%;
  padding: 20px;
}
.buttons-container button {
  background: rgba(77, 204, 132, 0.881);
  color: white;
  border: none;
  cursor: pointer;
  height: 2rem;
  width: 4rem;
  transition: 0.5s;
}
.buttons-container button:hover {
  background: white;
  color: rgba(77, 204, 132, 0.881);
}
</style>
