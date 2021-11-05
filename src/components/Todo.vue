<template>
  <div class="container">
    <h1>{{ title }}</h1>
    <input type="text" v-model="todoText" @keyup.enter="eventKeyup()">
    <div class="checkbox">
      <p class="list" v-for="todo in todos" :key="todo.id" :class="{ 'done': todo.value }">
        <input type="checkbox" v-model="todo.value" > {{ todo.name }}
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Todo',
  props: {
    title: {
      type: String,
      default: ''
    }
  },
  data() {
    return {
      todoText: '',
      todos: [
        {
          id: 1,
          name: 'Vue one',
          value: false,
        },
        {
          id: 2,
          name: 'Vue two',
          value: false,
        },
        {
          id: 3,
          name: 'Vue three',
          value: false,
        },
      ],
      todoId: 4,
    }
  },
  methods: {
    eventKeyup() {
      // enter input add todos
      this.todos.push({
        id: this.todoId++,
        name: this.todoText
      })
    },
  },
}
</script>

<style>
  .done {
    text-decoration: line-through;
  }
</style>