<template>
  <div id="app">
    <Todos />
  </div>
</template>

<script>
import Todos from './components/Todos';
export default {
  name: 'App',
  components: {
    Todos
  },
  data(){                 //data is a function that returns an object
    return {
      name:'todo List',
      todos:[             //todos is an element of the object that return data function
                          //todos value is an array of object(list of the todo items)
        {
          id:1,
          title:"Todo One",
          completed: false
        },
        {
          id:2,
          title:"Todo Two",
          completed: true
        },
        {
          id:3,
          title:"Todo Three",
          completed: false
        }
        
      ]
    }
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
</style>
