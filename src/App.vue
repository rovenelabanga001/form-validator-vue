<script setup lang="ts">
import RegistrationForm from "./components/RegistrationForm.vue";
import { provide, reactive } from "vue";

const showButtons = reactive({
  showPrevious: true,
  showNext: true,
});

provide("showButtons", showButtons);
</script>

<template>
  <RegistrationForm />
</template>
