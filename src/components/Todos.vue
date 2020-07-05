<template>
  <div>
    <div :key="todo.id" v-for="todo in todos">
      <Todo :todo="todo"></Todo>
    </div>
  </div>
</template>

<script>
import Todo from "./TodoItem";
export default {
  name: 'Todos',
  props: {
    todos: {
      type: Array,
    }
  },
  components: {
    Todo
  }

}
</script>

<style scoped>
</style>