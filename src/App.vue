<template>
  <div id="app">
    <Header />
    <br>
    <AddTodo v-on:add-todo="addTodo"/>
    <br>
    <h2>Following are todos:</h2>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>
import axios from 'axios';
import AddTodo from './components/AddTodo';
import Todos from './components/Todos';
import Header from './components/layout/Header';
export default {
  name: 'App',
  components: {
    Todos,
    Header,
    AddTodo

  },
  data(){                 //data is a function that returns an object
    return {
      name:'todo List',
      todos:[             //todos is an element of the object that return data function
                          //todos value is an array of object(list of the todo items)
        // {
        //   id:1,
        //   title:"Todo One",
        //   completed: false
        // },
        // {
        //   id:2,
        //   title:"Todo Two",
        //   completed: true
        // },
        // {
        //   id:3,
        //   title:"Todo Three",
        //   completed: false
        // }
        
      ]
    }
  },
  methods:{
        deleteTodo(id){
          axios.delete('https://jsonplaceholder.typicode.com/todos/'+id)
  .then(this.todos = this.todos.filter(todo=>todo.id!==id))
  .catch(err=>console.log(err));


          //this.todos = this.todos.filter(todo=>todo.id!==id); //without axios
        },

        addTodo(newTodo){
          const {id,title,completed}=newTodo; //const means construct
          //this.todos = [...this.todos, newTodo]; //it works without the axios
          axios.post('https://jsonplaceholder.typicode.com/todos',{
            id,
            title,
            completed
          })
            .then(res => this.todos=[...this.todos, res.data])
            .catch(err=>console.log(err));
      }
        
  },
  created() {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
  .then(res => this.todos=res.data)
  .catch(err=>console.log(err));
  }
}
</script>

<style>
* {
  box-sizing:border-box;
  margin:0;
  padding:0;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.5;
}

.btn {
  display: inline-block;
  border: none;
  background: green;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
  border-radius: 5px;
}

.btn:hover {
  background: #666;
}

#app{
  max-width: 600px;
  margin: auto;
  border: 2px solid #666;
  border-radius: 3px;
  padding: 3px;
}

.btn1 {
  display: inline-block;
  border: 2px;
  background: #bbb;
  color: black;
  padding: 7px 20px;
  border-radius: 5px;
}
</style>
