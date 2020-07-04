<template>
  <div>
    <div :key="todo.id" v-for="todo in todos">{{todo.title}}</div>
  </div>
</template>

<script>
export default {
  name: 'Todos',
  props: {
    todos: {
      type: Array,
    }
  }
}
</script>

<style scoped>
</style>