<script setup>
import { ref } from 'vue';
import AppExpensesList from './AppExpensesList.vue';
import AppBalance from './AppBalance.vue';

let expense = ref(0);
let balanceArray = ref([]);
let balance = ref(0);

const error = ref("Expense can't be 0");
let showError = ref(false);

const incomesList = ref([]);
const expensesList = ref([]);

const addExpense = () => {
  if (expense.value === 0) {
    showError.value = true;
  } else {
    showError.value = false;
    expense.value > 0
      ? incomesList.value.push(expense.value)
      : expensesList.value.push(expense.value);
  }

  balanceArray.value = expensesList.value.concat(incomesList.value);

  if (expensesList.value.length || incomesList.value.length) {
    balance.value = balanceArray.value.reduce((accumulator, currentValue) => {
      return accumulator + currentValue;
    });
  }
};
</script>
<template>
  <form @submit.prevent="addExpense">
    <p>
      To add an income put a positive number, to add an expense put a negative number. For float
      number use dot, not comma.
    </p>
    <input type="string" pattern="[0-9]+([,\.][0-9]+)?" v-model.number="expense" />
    <input type="submit" value="Add Expense / Income" />
    <p v-if="showError">{{ error }}</p>
  </form>
  <AppExpensesList :expense="expense" :incomesList="incomesList" :expensesList="expensesList" />
  <AppBalance :balance="balance" />
</template>

<style scoped>
form {
  display: flex;
  flex-flow: column;
  align-items: center;
}

input {
  box-sizing: border-box;
  height: 30px;
  width: 200px;
  margin: 3px;
  padding: 3px;
  border-radius: 5px;
}
</style>
