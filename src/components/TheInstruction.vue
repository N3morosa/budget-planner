<script setup>
import { ref } from 'vue';

const title = ref('Budget Planner');
</script>

<template>
  <div class="instruction">
    <h1>{{ title }}</h1>
    <p>To add an income put a positive number, to add an expense put a negative number.</p>
    <p>For float number use dot, not comma.</p>
    <p>To change a currency click $ sign below and edit it.</p>
  </div>
</template>

<style scoped>
.instruction {
  max-width: 500px;
  margin: 20px 0;
}
</style>
