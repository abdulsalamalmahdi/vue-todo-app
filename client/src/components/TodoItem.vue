<template>
  <div
    v-bind:class="{
      subcontainer: this.todo.completed === false,
      completed: this.todo.completed === true
    }"
  >
    <input @change="toggleCompleted" type="checkbox" />
    <h3>{{ todo.todo }}</h3>
    <span>{{ todo.posted }}</span>
    <button @click="$emit('del_todo', todo.id)">x</button>
  </div>
</template>

<script>
 import axios from "axios";
export default {
  name: "TodoItem",
  props: ["todo"],
  methods: {
    toggleCompleted() {
        const currentTodo={
            id: this.todo.id,
            todo:this.todo.todo,
            posted:this.todo.posted,
            completed: !this.todo.completed
        }
      this.todo.completed = !this.todo.completed;
      console.log(this.todo.completed);
      axios.put(`http://localhost:3000/todos/${this.todo.id}`, currentTodo )
    }
  }
};
</script>

<style scoped>
.subcontainer {
  display: flex;
  width: 100%;
  flex-flow: row nowrap;
  justify-content: center;
}

h3 {
  margin: 0;
}
span {
  font-size: 0.6em;
  width: 20%;
  align-self: center;
  margin: 0;
}
button {
  justify-self: flex-end;
  margin-left: auto;
  border-radius: 100%;
  border: 1px solid black;
  background-color: rgb(207, 100, 193);
  transition: width 1s;
}
button:hover {
  border-color: rgb(245, 161, 5);
  color: rgb(245, 161, 5);
  width: 5%;
}
.completed {
  background-color: green;
  display: flex;
  width: 100%;
  flex-flow: row nowrap;
  justify-content: center;
}
</style>
