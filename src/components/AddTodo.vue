<template>
  <input
    v-model="todoInputText"
    type="text"
    class="w-100 p-2"
    placeholder="type todo"
    @keyup.enter="addTodo"
  />
</template>

<script>
export default {
  props: {
    todoInputText: {
      type: Text,
      required: false,
    },
  },
  method: {
     addTodo(e) {
      const todoText = e.target.value;
      const todo = { id: this.todos.length === 0 ? 1 : this.todos[this.todos.length - 1].id + 1 , text: todoText, checked: false }
      this.todos = [...this.todos, todo];                 // ...문법을 이용해 add

      this.todoInputText = "";
    },
  }
};
</script>

<style>
</style>