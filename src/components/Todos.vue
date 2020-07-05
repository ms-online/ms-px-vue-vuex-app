<template>
  <div>
    <div :key="todo.id" v-for="todo in todos">
      <Todo :todo="todo" @delItem="$emit('handleItem',todo.id)"></Todo>
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
  },
  methods: {
    // delItem(id) {
    //   console.log(id)
    // }
  }

}
</script>

<style scoped>
</style>