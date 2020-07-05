<template>
  <form @submit.prevent="AddTodo">
    <input
      v-model="title"
      type="text"
      name="title"
      placeholder="请输入待办事项..."
    />
    <input type="submit" value="添加" class="btn" />
  </form>
</template>

<script>
const uuid = require('uuid');
export default {
  name: 'AddTodo',
  data() {
    return {
      title: '',
    };
  },
  methods: {
    AddTodo() {
      //   e.preventDefault();
      //   console.log(this.title)
      //   创建任务对象
      const newTodo = {
        id: uuid.v4(),
        title: this.title,
        complete: false,
      };
      console.log(newTodo);
      this.$emit('handleAdd', newTodo);
      this.title = '';
    },
  },
};
</script>

<style scoped>
form {
  display: flex;
}

input[type='text'] {
  flex: 10;
  padding: 5px;
}

input[type='submit'] {
  flex: 2;
}
</style>
