<template>
  <div>
      User TodoList
      <div v-for="user in users" :key="user.id">
          {{ user.name}}
  </div>
</template>

<script>
import axios from "axios";
import { mapState, mapActions } from 'vuex';
export default {
  created() {
    this.getusers();
  },
  computed: {
      ...mapState([
          'users',
          'todos'
      ]),
    users() {
      return this.$store.state.users;
    },
    todos() {
        return this.$store.state.todos;
    }
  },
  methods: {
      ...mapActions([
          'getUsers'
      ])
    getUsers() {
      this.$store.dispatch("getUsers");
    },
  },
};
</script>

<style>
</style>