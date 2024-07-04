<template>
     <h3>History</h3>
      <ul id="list" class="list">
        <li
         v-for="transaction in transactions" 
         :key="transaction.id" :class="transaction.amount < 0  ? 'minus': 'plus'">
          {{transaction.text}} <span>${{transaction.amount}}</span>
          <button @click="deleteTransaction(transaction.id)" class="delete-btn">x</button>
        </li>
      </ul>
</template>

<script setup>
// quest fa riferimento a props ref utilizzato in app e mi permette di rendere i miei data dinamici
// I have to use defineProps in the component that i'm passing trougth 

  import {defineProps} from 'vue';

  const emit = defineEmits(['transactionDeleted']);

  const props = defineProps({
    transactions: {
        type: Array,
        require: true,
    },
  });

  const deleteTransaction = (id) => {
    emit('transactionDeleted', id);
  };
</script>