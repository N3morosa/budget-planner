<script setup>
import { inject } from 'vue';
defineProps({
  transactionsList: {
    type: Array,
    required: true
  }
});

const currency = inject('currency');
const emit = defineEmits(['removeTransaction']);

const removeButtonClick = (id) => {
  emit('removeTransaction', id);
};
</script>

<template>
  <section v-if="transactionsList.length">
    <h2>List of transactions</h2>
    <ul>
      <li
        v-for="transactionsListItem in transactionsList"
        :key="transactionsListItem.id"
        :class="['list-item', transactionsListItem.amount > 0 ? 'income' : 'expense']"
      >
        {{ transactionsListItem.title }}:
        <span class="amount">
          {{ transactionsListItem.amount }}
          {{ currency }}
        </span>
        <button
          class="remove-button"
          type="button"
          @click="removeButtonClick(transactionsListItem.id)"
        >
          x
        </button>
      </li>
    </ul>
  </section>
</template>

<style scoped>
ul {
  --list-item-height: 30px;
  --list-item-padding: 5px;

  margin: 0;
  padding: 0;
  color: #000;
}
.list-item {
  padding: var(--list-item-padding);
  margin-bottom: 3px;
  position: relative;
  height: var(--list-item-height);
  line-height: var(--list-item-height);
}
.expense {
  background-color: #fbd0d9;
}
.income {
  background-color: #ccffe6;
}
.remove-button {
  box-sizing: content-box;
  height: var(--list-item-height);
  width: var(--list-item-height);
  padding: var(--list-item-padding);
  position: absolute;
  top: 0;
  right: calc((var(--list-item-height) + 2 * var(--list-item-padding)) * -1);
  border: none;
  color: #fff;
  background-color: #dc143c;
  font-weight: 700;
  opacity: 0;
  transition: opacity 0.5s linear;
}
.list-item:hover .remove-button {
  opacity: 1;
}

.amount {
  font-weight: bold;
}
</style>
