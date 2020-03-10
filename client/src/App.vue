<template>
  <div id="app">
    <TodoForm v-on:add_todo="addTodo" />
    <todos
     
      v-bind:todos="todos"
      v-on:del_todo="deleteTodo"
    />
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Todos from "./components/Todos";
import TodoForm from "./components/TodoForm.vue";
import axios from "axios";
export default {
  name: "App",
  components: {
    // HelloWorld,
    Todos,
    TodoForm
  },
  data() {
    return {
      todos: []
    };
  },
  methods: {
    deleteTodo(id) {
      axios
        .delete(`http://localhost:3000/todos/${id}`)
        .then(() => (this.todos = this.todos.filter(todo => todo.id !== id)))
        .catch(err => console.log(err));
      // console.log("kdjfk")
      //  this.todos= this.todos.filter(todo=> todo.id !== id);
    },
    addTodo({ id, todo, posted,completed }) {
      axios
        .post(`http://localhost:3000/todos`, {
          id,
          todo,
          posted,
          completed
        })
        .then(res => (this.todos = [...this.todos, res.data]))
        .then(() => console.log(this.todos))
        .catch(err => console.log(err));
    }
  },
  created() {
    axios
      .get("http://localhost:3000/todos")
      .then(res => (this.todos = res.data))
      .catch(err => console.log(err));
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
