<script setup>
import { ref } from 'vue';

const amount = ref('');
const title = ref('');

const emit = defineEmits(['transactionSubmitted']);

const error = ref("Inputs can't be empty");
const showError = ref(false);

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

    amount.value = '';
    title.value = '';
  }
};
</script>
<template>
  <form @submit.prevent="onSubmit">
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
  margin-bottom: 20px;
}

input {
  box-sizing: border-box;
  height: 40px;
  width: 250px;
  margin: 3px;
  padding: 5px;
  border-radius: 5px;
  border: 1px solid grey;
  font-family: 'Montserrat', sans-serif;
}

input[type='submit'] {
  background-color: #b0e0e6;
  border: none;
  font-weight: 700;
}
</style>
