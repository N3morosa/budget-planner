<script setup>
import { defineProps } from 'vue';
defineProps({
  expense: String,
  list: String
});

// console.log(list)
</script>

<template>
  <section>
    <h2>List of incomes and expenses</h2>
    <ul>
      <li v-for="listItem in list" :key="listItem">{{ listItem }}</li>
    </ul>
  </section>
</template>
