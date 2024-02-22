<script setup>
import Title from './components/Title.vue';
import Form from './components/Form.vue';
import TransactionsList from './components/TransactionsList.vue';
import Balance from './components/Balance.vue';

import { ref } from 'vue';

let transactionsList = ref([]);
let index = ref(0);
let sum = ref(0);

const handleTransaction = (transactionData) => {
  transactionsList.value.push({
    id: index.value + 1,
    title: transactionData.title,
    amount: transactionData.amount
  });
  console.log('OBJvALUES', Object.values(transactionData));

  sum.value = transactionsList.value.reduce((accumulator, transaction) => {
    return accumulator + transaction.amount;
  }, 0);
};
</script>

<template>
  <main>
    <Title />
    <Form @transactionSubmitted="handleTransaction" />
    <TransactionsList :transactionsList="transactionsList" />
    <Balance :sum="+sum" />
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
