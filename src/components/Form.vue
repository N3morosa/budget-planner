<script setup>
import { ref } from 'vue';

let amount = ref('');
let title = ref('');

let emit = defineEmits(['transactionSubmitted']);

const error = ref("Inputs can't be empty");
let showError = ref(false);

const onSubmit = () => {
  if (!amount.value || !title.value) {
    showError.value = true;
    return;
  } else {
    showError.value = false;
    const transactionData = {
      title: title.value,
      amount: amount.value
    };

    emit('transactionSubmitted', transactionData);
  }
};
</script>
<template>
  <form @submit.prevent="onSubmit">
    <p>
      To add an income put a positive number, to add an expense put a negative number. For float
      number use dot, not comma.
    </p>
    <input
      type="string"
      pattern="-?[0-9]+([,\.][0-9]+)?"
      v-model.number="amount"
      placeholder="Write an amount"
    />
    <input type="string" v-model="title" placeholder="Write a title of a transaction" />
    <input type="submit" value="Add Transaction" />
    <p v-if="showError">{{ error }}</p>
  </form>
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
