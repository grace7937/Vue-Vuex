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
  data() {
    return {
      todoInputText: "",
    };
  },
  method: {
    addTodo(e) {
      this.$emit("add-todo", e.target.value);
    },
  },
};
</script>

<style>
</style>