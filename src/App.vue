<script setup>
import {ref, onMounted, computed, watch} from 'vue'

const name = ref('')
const inputTodo = ref('')

watch(name, (newName) => {
  localStorage.setItem('name', newName)
})

onMounted(() => {
  name.value = localStorage.getItem('name') || ''
})

const addTodo = () => {

}

</script>

<template>
  <main class="app">
    <section class="greeting">
      <h2 class="title">Hello,
        <input type="text" placeholder="name" v-model="name">
      </h2>
    </section>

    <section class="create-todo">
      <h3>CREATE A TODO</h3>
      <form @submit.prevent="addTodo">
        <h4>What's on your todo list</h4>
        <input type="text" placeholder="todo" v-model="inputTodo">
        <h4>Pick a category</h4>
        <div class="options">
          <label>
            <input type="radio" name="category" value="business" class="category1">
            <span class="bubble business"></span>
            <div>Work</div>
          </label>
          <label>
            <input type="radio" name="category" value="personal" class="category2">
            <span class="bubble personal"></span>
            <div>Personal</div>
          </label>

        </div>
        <input type="submit" value="Add Todo">
      </form>
    </section>
  </main>
</template>

