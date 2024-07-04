<script setup>
import { ref } from 'vue'

const items = ref([
  {
    title: 'What is HTML?',
    content:
      'The HyperText Markup Language or HTML is the standard markup language for documents designed to be displayed in a web browser. It defines the content and structure of web content. It is often assisted by technologies such as Cascading Style Sheets and scripting languages such as JavaScript.',
    open: false
  },
  {
    title: 'What is CSS?',
    content:
      'Cascading Style Sheets is a style sheet language used for specifying the presentation and styling of a document written in a markup language such as HTML or XML. CSS is a cornerstone technology of the World Wide Web, alongside HTML and JavaScript.',
    open: false
  },
  {
    title: 'What is JS?',
    content:
      'JavaScript, often abbreviated as JS, is a programming language and core technology of the World Wide Web, alongside HTML and CSS. As of 2023, 98.7% of websites use JavaScript on the client side for webpage behavior, often incorporating third-party libraries.',
    open: false
  },
  {
    title: 'What is React?',
    content:
      'React is a free and open-source front-end JavaScript library for building user interfaces based on UI components. It is maintained by Meta (formerly Facebook) and a community of individual developers and companies.',
    open: false
  },
  {
    title: 'What is Vue.js?',
    content:
      'Vue.js is an open-source model–view–viewmodel front end JavaScript framework for building user interfaces and single-page applications. It was created by Evan You, and is maintained by him and the rest of the active core team members.',
    open: false
  },
  {
    title: 'What is Angular?',
    content:
      'Angular is a platform and framework for building single-page client applications using HTML and TypeScript. It is written in TypeScript and maintained by Google. Angular provides built-in features for HTTP services, routing, and more.',
    open: false
  },
  {
    title: 'What is Node.js?',
    content:
      'Node.js is an open-source, cross-platform, back-end JavaScript runtime environment that executes JavaScript code outside a web browser. Node.js lets developers use JavaScript to write command line tools and for server-side scripting.',
    open: false
  },
  {
    title: 'What is Python?',
    content:
      "Python is an interpreted, high-level and general-purpose programming language. Python's design philosophy emphasizes code readability with its notable use of significant indentation. It is widely used for web development, data analysis, artificial intelligence, and more.",
    open: false
  },
  {
    title: 'What is Java?',
    content:
      'Java is a high-level, class-based, object-oriented programming language that is designed to have as few implementation dependencies as possible. It is a general-purpose programming language intended to let application developers write once, run anywhere.',
    open: false
  },
  {
    title: 'What is Git?',
    content:
      'Git is a distributed version-control system for tracking changes in source code during software development. It is designed for coordinating work among programmers, but it can be used to track changes in any set of files.',
    open: false
  }
])

const toggleAccordion = (index) => {
  items.value = items.value.map((item, i) => ({
    ...item,
    open: i === index ? !item.open : false
  }))
}
</script>

<template>
  <div class="accordion-container">
    <div v-for="(item, index) in items" :key="index" class="accordion">
      <div class="accordion-header" @click="toggleAccordion(index)">
        {{ item.title }}
        <span class="arrow-icon">{{ item.open ? '▼' : '▶' }}</span>
      </div>
      <div v-show="item.open" class="accordion-content">
        {{ item.content }}
      </div>
    </div>
  </div>
</template>

<style scoped>
.accordion-container {
  max-width: 600px;
  margin: 50px auto;
}

.accordion {
  border: 1px solid #ddd;
  border-radius: 4px;
  overflow: hidden;
  margin-bottom: 10px;
}

.accordion-header {
  background-color: #3498db;
  color: #fff;
  padding: 15px;
  cursor: pointer;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.arrow-icon {
  font-size: 20px;
}

.accordion-content {
  padding: 15px;
  display: none;
  border-top: 1px solid #ddd;
  background-color: #f9f9f9;
  color: #333;
}

.accordion-content[style] {
  display: block;
}
</style>
