<script setup>
import { ref, onMounted } from 'vue'

const quotes = ref([
  {
    text: 'The only way to do great work is to love what you do.',
    author: 'Steve Jobs'
  },
  {
    text: "Believe you can and you're halfway there.",
    author: 'Theodore Roosevelt'
  },
  {
    text: "Life is what happens when you're busy making other plans.",
    author: 'John Lennon'
  },
  {
    text: 'Success is not final, failure is not fatal: It is the courage to continue that counts.',
    author: 'Winston Churchill'
  },
  {
    text: 'You miss 100% of the shots you don’t take.',
    author: 'Wayne Gretzky'
  },
  {
    text: "I have not failed. I've just found 10,000 ways that won't work.",
    author: 'Thomas Edison'
  },
  {
    text: 'The best way to predict the future is to invent it.',
    author: 'Alan Kay'
  },
  {
    text: 'It does not matter how slowly you go as long as you do not stop.',
    author: 'Confucius'
  },
  {
    text: 'Our greatest glory is not in never falling, but in rising every time we fall.',
    author: 'Confucius'
  },
  {
    text: 'Your time is limited, so don’t waste it living someone else’s life.',
    author: 'Steve Jobs'
  },
  {
    text: 'Don’t watch the clock; do what it does. Keep going.',
    author: 'Sam Levenson'
  },
  {
    text: 'The future belongs to those who believe in the beauty of their dreams.',
    author: 'Eleanor Roosevelt'
  },
  {
    text: 'It always seems impossible until it’s done.',
    author: 'Nelson Mandela'
  },
  {
    text: 'You are never too old to set another goal or to dream a new dream.',
    author: 'C.S. Lewis'
  },
  {
    text: 'The journey of a thousand miles begins with one step.',
    author: 'Lao Tzu'
  }
])

const currentQuote = ref({ text: '', author: '' })

const getRandomQuote = () => {
  const randomIndex = Math.floor(Math.random() * quotes.value.length)
  currentQuote.value = quotes.value[randomIndex]
}

// Get a random quote when the component is mounted
onMounted(getRandomQuote)
</script>

<template>
  <div class="quote-generator">
    <h1 class="app-title">Random Quote Generator</h1>

    <blockquote class="quote-container">
      <p>{{ currentQuote.text }}</p>
      <cite>{{ currentQuote.author }}</cite>
    </blockquote>

    <button @click="getRandomQuote" class="quote-button">Get Random Quote</button>
  </div>
</template>

<style scoped>
.quote-generator {
  max-width: 400px;
  margin: 50px auto;
  padding: 20px;
  text-align: center;
  border: 1px solid #ccc;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.app-title {
  font-size: 24px;
  margin-bottom: 20px;
  color: #333;
}

.quote-container {
  background-color: #f9f9f9;
  padding: 20px;
  border-radius: 8px;
  border: 1px solid #ddd;
  margin-bottom: 20px;
}

p {
  font-size: 18px;
  margin-bottom: 10px;
}

cite {
  font-style: normal;
  color: #777;
}

.quote-button {
  padding: 10px 20px;
  font-size: 16px;
  background-color: #3498db;
  color: #fff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.quote-button:hover {
  background-color: #2980b9;
}
</style>
