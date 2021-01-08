<template>
  <tr class="todo-item">
    <td>
      <input type="checkbox" name="isCompleted" v-on:change="markComplete" />
      <span v-bind:class="{ isCompleted: todoItem.completed }">{{
        todoItem.id
      }}</span>
    </td>
    <td>
      <p v-bind:class="{ isCompleted: todoItem.completed }">
        {{ todoItem.title }}
      </p>
    </td>
    <td>
      {{ todoItem.completed }}
    </td>
    <td>
        <button class="del" @click="$emit('del-todoItem', todoItem.id)">x</button>
    </td>
  </tr>
</template>

<script>
export default {
  name: "TodoItem",
  props: {
    todoItem: {
      id: Number,
      title: String,
      completed: Boolean,
    },
  },
  methods: {
    markComplete() {
      this.todoItem.completed = !this.todoItem.completed;
    },
  },
};
</script>

<style>
.todo-item {
  background: #f4f4f4;
  padding: 10px;
  border-bottom: 1px #ccc dotted;
}
.isCompleted {
  text-decoration: line-through;
}
.del {
    background: #ff0000;
    color: #fff;
    border: none;
    padding: 5px 9px;
    border-radius: 50%;
    cursor: pointer;
    float: right;
  }
</style>