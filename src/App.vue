<template>
  <div id="app" class="container">
    <h1 class="text-center">Todo App</h1>
    <CompletedTodo />
    <AddTodo @add-todo="addTodo" />
    <hr />
    <TodoList
      :todoInputText="todoInputText"
      :todos="todos"
      @toggole-checkbox="toggleCheckbox"
      @remove-todo="removeTodo"
    />
  </div>
</template>

<script>
import AddTodo from "../src/components/AddTodo.vue";
import TodoList from "../src/components/TodoList.vue";
import CompletedTodo from "../src/components/CompletedTodo.vue";

export default {
  components: {
    TodoList,
    AddTodo,
    CompletedTodo,
  },
  data() {
    return {
      todoInputText: "",
      todos: [],
    };
  },

  methods: {
    addTodo(e) {
      const todoText = e.target.value;
      const todo = {
        id:
          this.todos.length === 0
            ? 1
            : this.todos[this.todos.length - 1].id + 1,
        text: todoText,
        checked: false,
      };
      this.todos = [...this.todos, todo]; // ...문법을 이용해 add

      this.todoInputText = "";
    },
    removeTodo(id) {
      const index = this.todos.findIndex((todo) => {
        return todo.id === id;
      });
      this.todos.splice(index, 1); //splice를 이용해 remove
    },
    toggleCheckbox({ id, checked }) {
      console.log(id, checked);
      const index = this.todos.findIndex((todo) => {
        return todo.id === id;
      });
      this.todos[index].checked = checked;
    },
  },
};
</script>

