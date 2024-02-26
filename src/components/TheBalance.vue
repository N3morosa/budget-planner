<script setup>
import TransactionsCurrency from '@/components/TransactionsCurrency.vue';
defineProps({
  sum: {
    type: Number,
    required: true
  }
});
</script>

<template>
  <div class="balance">
    <p>Balance: {{ sum.toFixed(2) }}</p>
    <TransactionsCurrency />
  </div>
</template>

<style scoped>
p {
  margin: 0;
}

.balance {
  display: flex;
  align-items: center;
  margin-bottom: 40px;
  color: #000;
  font-size: 20px;
  font-weight: 700;
}
</style>
