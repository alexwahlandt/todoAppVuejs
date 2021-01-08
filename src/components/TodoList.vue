<template>
  <div>
    <table class="todoList__table">
      <tr>
        <th>ID</th>
        <th>Title</th>
        <th>Completed</th>
      </tr>
      <todo-item
        v-for="todo in todos"
        :key="todo.id"
        :todoItem="todo"
        v-on="$listeners"
      />
    </table>
  </div>
</template>

<script>

import TodoItem from "./TodoItem.vue";
export default {
  components: { TodoItem },
  name: "TodoList",
  methods: {
    
  },
  props: {
    todos: {
      type: Array,
      validator: (list) =>
        list.every(
          (elem) =>
            typeof elem.id === "number" &&
            typeof elem.title === "string" &&
            typeof elem.completed === "boolean"
        ),
    },
  },
};
</script>

<style>
.todoList__table {
  width: 100%;
}
</style>