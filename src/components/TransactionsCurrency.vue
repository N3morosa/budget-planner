<script setup>
import { inject } from 'vue';

const currency = inject('currency');
</script>

<template>
  <span contenteditable="true" class="currency">
    {{ currency }}
  </span>
</template>

<style scoped>
.currency {
  cursor: pointer;
}
</style>
