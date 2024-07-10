<script setup>
import { ref, computed, onMounted } from 'vue'
import AddTransactionVue from './components/AddTransaction.vue'
import BalanceComponentVue from './components/BalanceComponent.vue'
import Header from './components/HeaderComponent.vue'
import IncomeExpansesVue from './components/IncomeExpanses.vue'
import TransactionList from './components/TransactionList.vue'
import { useToast } from 'vue-toastification'
const toast = useToast()

const transactions = ref([])

onMounted(() => {
  const savedTransactions = JSON.parse(localStorage.getItem('transactions'))

  if (savedTransactions) {
    transactions.value = savedTransactions
  }
})

// to get total
const total = computed(() => {
  return transactions.value.reduce((acc, transaction) => {
    return acc + transaction.amount
  }, 0)
})
// to get income
const income = computed(() => {
  return transactions.value
    .filter((transaction) => transaction.amount > 0)
    .reduce((acc, transaction) => {
      return acc + transaction.amount
    }, 0)
    .toFixed(2)
})
// to get expanses
const expanses = computed(() => {
  return transactions.value
    .filter((transaction) => transaction.amount < 0)
    .reduce((acc, transaction) => {
      return acc + transaction.amount
    }, 0)
    .toFixed(2)
})

// Submit transaction
const handleTransactionSubmitted = (transactionData) => {
  transactions.value.push({
    id: generateUniqueId(),
    text: transactionData.text,
    amount: transactionData.amount
  })

  saveTransactionsToLocalStorage()

  toast.success('Transaction added.')
}

// Generate unique ID
const generateUniqueId = () => {
  return Math.floor(Math.random() * 1000000)
}

// Delete transaction
const handleTransactionDeleted = (id) => {
  transactions.value = transactions.value.filter((transaction) => transaction.id !== id)

  saveTransactionsToLocalStorage()

  toast.success('Transaction deleted.')
}

// Save transactions to local storage
const saveTransactionsToLocalStorage = () => {
  localStorage.setItem('transactions', JSON.stringify(transactions.value))
}
</script>

<template>
  <Header />
  <BalanceComponentVue :total="+total" />
  <IncomeExpansesVue :income="+income" :expanses="+expanses" />
  <TransactionList :transactions="transactions" @transactionDeleted="handleTransactionDeleted" />
  <AddTransactionVue @transactionSubmitted="handleTransactionSubmitted" />
</template>
