<script setup>
defineProps({
  transactionsList: {
    type: Array,
    required: true,
  }
});
</script>

<template>
  <section v-if="transactionsList.length">
    <h2>List of transactions</h2>
    <ul>
      <li v-for="transactionsListItem in transactionsList" :key="transactionsListItem.id">
        {{ transactionsListItem.title }} {{ transactionsListItem.amount }} PLN
      </li>
    </ul>
  </section>
</template>
