<template>
  <div class="admin-dashboard">
    <nav>
      <router-link to="/admin/products">Керування продуктами</router-link> |
      <router-link to="/admin/reviews">Відгуки</router-link>
    </nav>
    <main>
      <router-view></router-view>
    </main>
  </div>
</template>

<script>
export default {
  name: 'AdminDashboard',
};
</script>

<style scoped>
nav {
  padding: 10px;
  background-color: #f0f0f0;
}
nav a {
  margin-right: 10px;
  text-decoration: none;
  color: #333;
}
main {
  padding: 20px;
}
</style>
