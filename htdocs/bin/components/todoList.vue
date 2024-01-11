<template>
  <div>
    <input v-model="newTodo" />
    <button @click="addTodo">Add Todo</button>
    <ul>
      <li v-for="(todo, index) in todos" :key="index">
        {{ todo }}
        <button @click="removeTodo(index)">Remove</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodo: ''
    };
  },
  computed: {
    todos() {
      return this.$store.getters.getTodos;
    }
  },
  methods: {
    addTodo() {
      this.$store.dispatch('addTodoAsync', this.newTodo);
      this.newTodo = '';
    },
    removeTodo(index) {
      this.$store.dispatch('removeTodoAsync', index);
    }
  }
};
</script>
