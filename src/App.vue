<template>
  <HeaderC />
  <div class="container">
    <Balance :total="total" />
    <IncomeExpenses v-bind:income="+income" v-bind:expenses="+expenses" />
    <TransactionList v-bind:transactions="transactions" />
    <AddTransaction />
  </div>
</template>

<script setup>
import Header from './components/Header.vue';
import Balance from './components/Balance.vue';
import IncomeExpenses from './components/IncomeExpenses.vue';
import TransactionList from './components/TransactionList.vue';
import AddTransaction from './components/AddTransaction.vue';
import { ref, computed } from 'vue';
const transactions = ref([
  { id: 1, text: 'Headphones', amount: -119.99 },
  { id: 1, text: 'Books', amount: -89.99 },
  { id: 1, text: 'Salary', amount: 8930.84 },
  { id: 1, text: 'Laptop', amount: -419.99 },
  { id: 1, text: 'Mouse', amount: -54.99 }
]);
//Get total
const total = computed(() => {
  return transactions.value
    .reduce((acc, transaction) => {
      return acc + transaction.amount;
    }, 0)
    .toFixed(2);
});

//Get Income
const income = computed(() => {
  return transactions.value
    .filter((transaction) => transaction.amount > 0)
    .reduce((acc, transaction) => {
      return acc + transaction.amount;
    }, 0)
    .toFixed(2);
});

//Get Expenses

const expenses = computed(() => {
  return transactions.value
    .filter((transaction) => transaction.amount < 0)
    .reduce((acc, transaction) => {
      return acc + transaction.amount;
    }, 0)
    .toFixed(2);
});
</script>
