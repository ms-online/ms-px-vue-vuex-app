<template>
  <div id="app">
    <!-- Header -->
    <Header />
    <!-- <div v-bind:key="todo.id" v-for="todo in todos">{{todo.id}} - {{todo.title}}</div> -->
    <Todos :todos="todos" @handleItem="handleItem" />
  </div>
</template>

<script>
import Header from './components/layout/Header.vue';
import Todos from "./components/Todos.vue"
export default {
  name: 'app',
  data() {
    return {
      title: "米修在线",
      todos: [
        {
          id: 1,
          title: "待办事项1",
          complete: false
        },
        {
          id: 2,
          title: "待办事项2",
          complete: false
        },
        {
          id: 3,
          title: "待办事项3",
          complete: false
        }
      ]
    }
  },
  components: {
    Todos,
    Header
  },
  methods: {
    handleItem(id) {
      // console.log(id);
      this.todos = this.todos.filter(todo => todo.id != id)
    }
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}
</style>
