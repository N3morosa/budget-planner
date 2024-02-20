<script setup>
import { ref } from 'vue';
import AppExpensesList from './AppExpensesList.vue';

let expense = ref('');
const list = ref([]);

const addExpense = () => {
  list.value.push(expense.value);
};
</script>
<template>
  <form @submit.prevent="addExpense">
    <input type="number" v-model="expense" />
    <button type="submit">Add Expense / Income</button>
    <p>{{ expense }}</p>
  </form>
  <AppExpensesList :expense="expense" :list="list" />
</template>
