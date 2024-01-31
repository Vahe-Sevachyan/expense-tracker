<template>
  <h3>History</h3>
  <ul id="list" class="list">
    <li
      v-for="transaction in transactions"
      v-bind:key="transaction.id"
      v-bind:class="transaction.amount < 0 ? 'minus' : 'plus'"
    >
      {{ transaction.text }} <span>${{ transaction.amount }}</span
      ><button v-on:click="deleteTransaction(transaction.id)" class="delete-btn">X</button>
    </li>
    <!-- <li class="minus">Laptop <span>$400</span><button class="delete-btn">X</button></li>
    <li class="plus">PayCheck <span>$20,000</span><button class="delete-btn">X</button></li> -->
  </ul>
</template>
<script setup>
defineProps({
  transactions: {
    type: Array,
    required: true
  }
});
const emit = defineEmits(['transactionDeleted']);
const deleteTransaction = (id) => {
  emit('transactionDeleted', id);
};
</script>
