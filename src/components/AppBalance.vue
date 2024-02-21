<script setup>
import { defineProps } from 'vue';
defineProps({
  balance: {
    type: Number,
    default: 0
  }
});
</script>

<template>
  <p>Balance : {{ balance }}</p>
</template>
