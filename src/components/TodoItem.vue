<template>
  <div class="todo-item" :class="{'is-complete':todo.complete}">
    <p>
      <input type="checkbox" @change="markComplate" />
      {{todo.title}}
      <button class="del" @click="$emit('delItem',todo.id)">x</button>
    </p>
  </div>
</template>

<script>
export default {
  name: 'Todo',
  props: ["todo"],
  methods: {
    markComplate() {
      this.todo.complete = !this.todo.complete
    }
  }

}
</script>

<style scoped>
.todo-item {
  background: #f4f4f4;
  padding: 10px;
  border-bottom: 1px solid #ccc;
}

.is-complete {
  text-decoration: line-through;
}

.del {
  background: #ff0000;
  color: #fff;
  border: none;
  padding: 5px 9px;
  border-radius: 50%;
  cursor: pointer;
  float: right;
}
.del:focus {
  outline: none;
}
</style>