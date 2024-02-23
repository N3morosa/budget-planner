<script setup>
defineProps({
  sum: {
    type: Number,
    required: true
  }
});
</script>

<template>
  <div class="balance">
    <p>Balance: {{ sum.toFixed(2) }} PLN</p>
  </div>
</template>

<style scoped>
.balance {
  margin-bottom: 40px;
  color: #fff;
  font-size: 20px;
  font-weight: 700;
}

p {
  margin: 0;
}
</style>
