<template>
    <div>
        <form @submit="addTodo">
            <p> <b>Add Todo item:</b> <input type="text" v-model="title" name="title" placeholder="Add todo...." class="btn1"></p>
            <input type="submit" value="Submit" class="btn btn-success ">
        </form>
    </div>
</template>

<script>
//import { v4 as uuidv4 } from 'uuid';   //this line is used for generating a random id
export default {
    name:"AddTodo",
    data(){
        return {
            title:''
        }
    },
    methods: {

        addTodo(e){
            e.preventDefault();
            const newTodo = {
                id:this.id,  ////this line is used for generating a random id
                title:this.title,
                completed:false
            }
            //Send up to parent
            this.$emit('add-todo',newTodo);
            this.title="";
        },
    }
}
</script>

<style scoped>
    form {
        display: flex;
    }

    




</style>