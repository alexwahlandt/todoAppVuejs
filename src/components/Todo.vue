<template>
  <div>
    <h1>Todo App</h1>
    <AddTodo @addTodoItem="addItem" />
    <div>
      <PulseLoader v-if="loading" />
      <TodoList v-else v-bind:todos="todos" @del-todoItem="delItem" />
    </div>
  </div>
</template>

<script>
import TodoList from "./TodoList";
import AddTodo from "./AddTodo.vue";
import PulseLoader from "vue-spinner/src/PulseLoader.vue";
export default {
  name: "Todo",
  components: {
    TodoList,
    AddTodo,
    PulseLoader,
  },
  props: { todosProps: Array, loading: Boolean },
  data() {
    return {
      todos: Array,
    };
  },
  methods: {
    delItem(id) {
      console.log("delete item", id);
      this.todos = this.todos.filter((todo) => todo.id !== id);
    },
    addItem(todoItem) {
      this.todos.push(todoItem);
    },
  },
  watch: { 
    todosProps: function () {
    console.log("props",this.todosProps)
    this.todos = this.todosProps;
  },
  }
};
</script>

<style>
</style>