<template>
  <div class="main">
    <div class="container" v-bind:key="todo.id" v-for="todo in todos">
      <TodoItem v-bind:todo="todo" v-on:del_todo="$emit('del_todo', todo.id)"/>
    </div>
  </div>
</template>

<script>
 import TodoItem from './TodoItem.vue'
export default {
  name: "Todos",
  components: {
        TodoItem
  },
  props: ["todos"],
  
  }
</script>

<style scoped>
.main{
    position: relative;
    display: flex;
    flex-direction: column;
    align-items: center;
   
}
.container{
    display: flex;
    flex-direction: row;
    flex-wrap: nowrap;
    border: 1px solid black;
    justify-content: center;
    background-color: rgb(159, 92, 221);
    width:50%;
    
    
}
</style>
