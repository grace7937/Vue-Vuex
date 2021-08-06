<template>
<div>
  <Todo :todos="todos" v-for="(todo, index) in todos" :key="index" :todo="todo" @toggle-checkbox="toggleCheckbox" @remove-todo="removeTodo"/>
</div>
</template>

<script>
import Todo from "./Todo.vue"

export default {
    components: {
        Todo,
    },
    props: {
        todos: {
            type: Array,
            required: true
        }
    },
    methods: {
        toggleCheckbox(valu) {
            this.$emit('toggle-checkbox', value)
        },
        removeTodo(todoId) {
            this.$emit('remove-todo', todoId)
        } 
    }

}
</script>

<style>

</style>