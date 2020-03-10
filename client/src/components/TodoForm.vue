<template>

    <div>
    <form @submit.prevent="add">
        <input v-model="todo" type="text" name="todo">
        <input  type="submit" value="add"/>
    </form>
    </div>
</template>

<script>
import { v4 as uuidv4 } from 'uuid';
export default {
    name:"TodoForm",
    data(){
        return {
            todo:""
        }
    },
    methods:{
        add(){
           //v-on:submit.prevent="add"
           const newTodo= {
               id:uuidv4(),
               todo: this.todo,
               posted:JSON.stringify(new Date(Date.now())).split("").splice(0,20).join("").replace(/T/, "-").replace(`"`,""),
               completed: false,
           }
            this.$emit("add_todo", newTodo);
            this.todo="";

        }
    }
}
</script>

<style scoped>

</style>