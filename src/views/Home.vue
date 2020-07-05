<template>
  <div id="app">
    <!-- AddTodo -->
    <AddTodo @handleAdd="handleAdd" />
    <!-- <div v-bind:key="todo.id" v-for="todo in todos">{{todo.id}} - {{todo.title}}</div> -->
    <Todos :todos="todos" @handleItem="handleItem" />
  </div>
</template>

<script>
import axios from 'axios';

import AddTodo from '../components/AddTodo.vue';
import Todos from '../components/Todos.vue';
export default {
  name: 'Home',
  data() {
    return {
      title: '米修在线',
      todos: [],
    };
  },
  components: {
    Todos,
    AddTodo,
  },
  methods: {
    handleItem(id) {
      // console.log(id);
      // 删除任务
      axios
        .delete(`http://jsonplaceholder.typicode.com/todos/${id}`)
        .then((res) => {
          this.todos = this.todos.filter((todo) => todo.id != id);
        })
        .catch((err) => console.log(err));
    },
    handleAdd(newTodo) {
      // this.todos.unshift(newTodo);
      // 结构添加的数据
      const { title, complete } = newTodo;
      axios
        .post('http://jsonplaceholder.typicode.com/todos', {
          title,
          complete,
        })
        .then((res) => (this.todos = [res.data, ...this.todos]))
        .catch((err) => console.log(err));
    },
  },
  //   使用created钩子函数，在加载的时候请求数据
  created() {
    axios
      .get('http://jsonplaceholder.typicode.com/todos?_limit=15')
      .then((res) => {
        // console.log(res);
        this.todos = res.data;
      })
      .catch((err) => console.log(err));
  },
};
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
.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}
.btn:focus {
  outline: none;
}
</style>
