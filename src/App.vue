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

const total = computed(() => {
  return transactions.value.reduce((acc, transaction) => {
      return acc + transaction.amount;
  }, 0);
})

const income = computed(() => {
  return transactions.value.filter((trx) => trx.amount > 0)
})
</script>

<template>
  <Header />
  <div class="container">
    <Balance :total="total"/>
    <IncomeExpense :income= "income" />
    <TransactionHistory :transactions = "transactions"/>
    <AddTransaction />
  </div>
</template>


