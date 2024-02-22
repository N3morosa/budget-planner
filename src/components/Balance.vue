<script setup>
defineProps({
  sum: {
    type: Number,
    required: true,
  }
});
</script>

<template>
  <p>Balance: {{ sum }}</p>
</template>
