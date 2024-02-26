<script setup>
import { ref, onMounted } from 'vue';

const currency = ref('$');

const addCurrencyToLocalStorage = () => {
  localStorage.setItem('currency', JSON.stringify(currency.value));
};

onMounted(() => {
  const existingCurrency = JSON.parse(localStorage.getItem('currency'));

  if (existingCurrency) {
    currency.value = existingCurrency;
  }
});
</script>

<template>
  <input
    type="text"
    class="currency"
    v-model="currency"
    @blur="addCurrencyToLocalStorage"
    size="3"
  />
</template>

<style scoped>
.currency {
  border: none;
  background-color: transparent;
  font-family: 'Montserrat', sans-serif;
  font-size: 20px;
  font-weight: 700;
}
</style>
