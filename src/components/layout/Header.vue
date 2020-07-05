<template>
  <header class="header">
    <h1>待办事项</h1>
    <!-- 路由切换 -->
    <div id="nav">
      <router-link to="/">主页</router-link>
      <router-link to="/about">关于</router-link>
    </div>
  </header>
</template>

<script>
export default {
  name: 'Header',
};
</script>

<style scoped>
.header {
  background: #333;
  color: white;
  padding: 10px;
  text-align: center;
}

.header a {
  color: white;
  padding-right: 5px;
  text-decoration: none;
}
</style>
