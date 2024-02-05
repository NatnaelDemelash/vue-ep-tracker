<script setup>
import Header from './components/Header.vue';
import Balance from './components/Balance.vue';
import IncomeExpense from './components/IncomeExpense.vue';
import TransactionHistory from './components/TransactionHistory.vue';
import AddTransaction from './components/AddTransaction.vue';

import { ref, computed } from 'vue';
const transactions = ref([
    {id: 1, text: 'Flower', amount: -23.87},
    {id: 2, text: 'Salary', amount: 357.34},
    {id: 3, text: 'Book', amount: -13.32},
]);

// Get total
const total = computed(() => {
  return transactions.value.reduce((acc, transaction) => {
      return acc + transaction.amount;
  }, 0);
})

// Get Income
const income = computed(() => {
  return transactions.value.filter((transaction) => transaction.amount > 0)
  .reduce((acc, transaction) => {
    return  acc + transaction.amount
  }, 0).toFixed(2);
})

// Get Expenses
const expenses = computed(() => {
  return transactions.value.filter((transaction) => transaction.amount < 0)
  .reduce((acc, transaction) => {
    return acc + transaction.amount
  },0).toFixed(2);
})


</script>

<template>
  <Header />
  <div class="container">
    <Balance :total="total"/>
    <IncomeExpense :income= "income" :expenses="expenses"/>
    <TransactionHistory :transactions = "transactions"/>
    <AddTransaction />
  </div>
</template>


