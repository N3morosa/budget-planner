<script setup>
import { defineProps } from 'vue';
defineProps({
  expense: Number || String,
  expensesList: Array,
  incomesList: Array
});
</script>

<template>
  <article>
    <section v-if="expensesList.length">
      <h2>List of expenses</h2>
      <ul>
        <li v-for="(expensesListItem, index) in expensesList" :key="index">
          {{ expensesListItem }}
        </li>
      </ul>
    </section>
    <section v-if="incomesList.length">
      <h2>List of incomes</h2>
      <ul>
        <li v-for="(incomesListItem, index) in incomesList" :key="index">{{ incomesListItem }}</li>
      </ul>
    </section>
  </article>
</template>
