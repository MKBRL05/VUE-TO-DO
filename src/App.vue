<template>
  <div id="app">
    <h1>Vue To-Do App</h1>
    <div class="input-container">
      <input v-model="newTodo" placeholder="Füge eine neue Aufgabe hinzu" @keyup.enter="addTodo" />
      <button @click="addTodo">Hinzufügen</button>
    </div>
    <ul>
      <li v-for="(todo, index) in todos" :key="index" class="todo-item">
        <input type="checkbox" v-model="todo.done" />
        <span :class="{ done: todo.done }">{{ todo.text }}</span>
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
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim() !== '') {
        this.todos.push({ text: this.newTodo, done: false });
        this.newTodo = '';
      }
    },
    removeTodo(index) {
      this.todos.splice(index, 1);
    }
  }
};
</script>

<style scoped>
#app {
  max-width: 600px;
  margin: 50px auto;
  font-family: 'Poppins', sans-serif;
  text-align: center;
  background: linear-gradient(to right, #ff7e5f, #feb47b);
  border-radius: 15px;
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
  padding: 20px;
  color: #fff;
}
.input-container {
  display: flex;
  margin-bottom: 20px;
  gap: 10px;
}
input {
  flex: 1;
  padding: 15px;
  font-size: 16px;
  border: 2px solid #ff6b6b;
  border-radius: 5px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  transition: border-color 0.3s ease;
}
input:focus {
  border-color: #ff4757;
}
button {
  padding: 15px;
  font-size: 16px;
  cursor: pointer;
  background: #ff6b6b;
  border: none;
  border-radius: 5px;
  color: #fff;
  transition: background 0.3s ease;
}
button:hover {
  background: #ff4757;
}
ul {
  list-style-type: none;
  padding: 0;
}
.todo-item {
  display: flex;
  align-items: center;
  justify-content: left;
  background: #fff;
  color: #333;
  padding: 15px;
  border-radius: 5px;
  margin-bottom: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  width: 100%;
  box-sizing: border-box;
}
.todo-item input[type="checkbox"] {
  width: 10px;
  transform: scale(1.2);
  margin-right: 50%;
}
.done {
  text-decoration: line-through;
  color: #999;
}
button:focus, input:focus {
  outline: none;
}
</style>
