<template>
  <div class="container">
    <h1>📝 Vue Todo App</h1>

    <input v-model="newTodo" @keyup.enter="addTodo" placeholder="Add a task..." />
    <button @click="addTodo">Add</button>

    <ul>
      <li v-for="(todo, index) in todos" :key="index">
        {{ todo }}
        <button @click="removeTodo(index)">❌</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodo: '',
      todos: []
    }
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim() !== '') {
        this.todos.push(this.newTodo.trim())
        this.newTodo = ''
      }
    },
    removeTodo(index) {
      this.todos.splice(index, 1)
    }
  }
}
</script>

<style scoped>
.container {
  max-width: 400px;
  margin: 30px auto;
  text-align: center;
}
input {
  padding: 8px;
  width: 70%;
}
button {
  padding: 8px 12px;
  margin-left: 5px;
}
ul {
  list-style: none;
  padding: 0;
}
li {
  text-align: left;
  margin: 8px 0;
  background: #f1f1f1;
  padding: 6px 10px;
  border-radius: 4px;
}
</style>
