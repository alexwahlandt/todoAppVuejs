<template>
  <div>
    <input
      type="text"
      name="addTodoItem"
      v-model="title"
      placeholder="Type new title"
    />
    <button type="submit" v-on:click="createTodoItem">Submit</button>
  </div>
</template>

<script>
import { v4 as uuidv4 } from "uuid";
export default {
  name: "AddTodo",
  data() {
    return {
      title: "",
      id: -1,
      completed: false,
    };
  },
  methods: {
    createTodoItem: function (e) {
      e.preventDefault();
      const newTodoItem = {
        title: this.title,
        id: parseInt(uuidv4()),
        completed: this.completed,
      };
      this.$emit('addTodoItem', newTodoItem);
    },
  },
};
</script>

<style>
</style>