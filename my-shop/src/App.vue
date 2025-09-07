<template>
  <div id="app">
    <ProductList />
    <FooterComponent />
  </div>
</template>

<script>
import ProductList from './components/ProductList.vue';
import FooterComponent from './components/FooterComponent.vue';

export default {
  name: 'App',
  components: {
    ProductList,
    FooterComponent
  }
};
</script>

<style>
#app {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

#app > *:not(:last-child) {
  flex-shrink: 0;
}
</style>
