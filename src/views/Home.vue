<template>
  <div class="home">
    <Todo v-bind:todosProps="todos" v-bind:loading="loading"/>
  </div>
</template>

<script>
import Todo from '../components/Todo'
import axios from 'axios'

export default {
  name: 'Home',
  components: {
    Todo
  },
  data: function () {
    return{
      todos:[],
       loading: true,
    }
  },
  created: function() {
    const url = "https://jsonplaceholder.typicode.com/todos?_limit=5"
    axios.get(url)
    .then(res => {
      this.todos = res.data;
      console.log("res.data",this.todos)
      this.loading = false;
    })
    .catch(error => {
      console.log(error)
    })
  }
}
</script>
<style>
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }
  body {
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
  }
  .btn {
    display: inline-block;
    border: none;
    background: #555;
    color: #fff;
    padding: 7px 20px;
    cursor: pointer;
  }
  .btn:hover {
    background: #666;
  }
</style>