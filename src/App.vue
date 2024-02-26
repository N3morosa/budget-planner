<script setup>
import TheInstruction from '@/components/TheInstruction.vue';
import TheForm from '@/components/TheForm.vue';
import TheTransactionsList from '@/components/TheTransactionsList.vue';
import TheBalance from '@/components/TheBalance.vue';

import { ref, computed, onMounted } from 'vue';

const transactionsList = ref([]);

const handleTransactionAdd = (transactionData) => {
  const { amount, title } = transactionData;

  transactionsList.value.push({
    id: amount + title,
    title: title,
    amount: amount
  });

  addTransactionsListToLocalStorage();
};

const handleTransactionRemove = (id) => {
  transactionsList.value = transactionsList.value.filter((transaction) => {
    return transaction.id !== id;
  });

  addTransactionsListToLocalStorage();
};

let sum = computed(() => {
  return transactionsList.value.reduce((accumulator, transaction) => {
    return accumulator + transaction.amount;
  }, 0);
});

const addTransactionsListToLocalStorage = () => {
  localStorage.setItem('transactionsList', JSON.stringify(transactionsList.value));
};

onMounted(() => {
  const existingTransactionsList = JSON.parse(localStorage.getItem('transactionsList'));

  if (existingTransactionsList) {
    transactionsList.value = existingTransactionsList;
  }
});
</script>

<template>
  <main>
    <TheInstruction />
    <TheBalance :sum="+sum" />
    <TheForm @transactionSubmitted="handleTransactionAdd" />
    <TheTransactionsList
      :transactionsList="transactionsList"
      @removeTransaction="handleTransactionRemove"
    />
  </main>
</template>

<style scoped>
main {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
