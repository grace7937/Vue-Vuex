<template>
  <div>
    <input type="checkbox" :checked="todo.checked" @change="toggleCheckbox" />
    <span class="ml-3 flex-grow-1"
          :class="todo.checked ? 'text-muted':''"
          :style="todo.checked ? 'text-decoreation-line-throug' : ''"
    >{{ todo.text }}</span>
    <span><button @click="removeTodo">X</button></span>
  </div>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true,
    },
    todos: {
      type: Array,
      required: false,
    },
  },
  methods: {
    removeTodo() {
      this.$emit("remove-todo", this.todo.id )
    },
    toggleCheckbox(e) {
        this.$emit('toggle-checkbox', {id: this.todo.id , checked: e.target.checked })
    }
  },
};
</script>

<style>
</style>