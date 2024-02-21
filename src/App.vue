<script setup>
import AppTitle from './components/AppTitle.vue';
import AppForm from './components/AppForm.vue';
</script>

<template>
  <main>
    <AppTitle />
    <AppForm />
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
