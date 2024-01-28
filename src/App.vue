<template>
  <HeaderC />
  <div class="container">
    <BalanceC />
    <IncomeExpenses />
    <TransactionList />
    <AddTransaction />
  </div>
</template>

<script>
import HeaderC from './components/HeaderC.vue'
import BalanceC from './components/BalanceC.vue'
import IncomeExpenses from './components/IncomeExpenses.vue'
import TransactionList from './components/TransactionList.vue'
import AddTransaction from './components/AddTransaction.vue'
export default {
  components: {
    HeaderC,
    BalanceC,
    IncomeExpenses,
    TransactionList,
    AddTransaction
  }
}
</script>
