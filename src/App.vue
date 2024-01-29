<template>
  <HeaderC />
  <div class="container">
    <BalanceC :total="total" />
    <IncomeExpenses />
    <TransactionList v-bind:transactions="transactions" />
    <AddTransaction />
  </div>
</template>

<script setup>
import HeaderC from './components/HeaderC.vue';
import BalanceC from './components/BalanceC.vue';
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

const total = computed(() => {
  return transactions.value.reduce((acc, transaction) => {
    return acc + transaction.amount;
  }, 0);
});
</script>
