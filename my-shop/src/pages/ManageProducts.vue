<template>
  <div>
    <h2>Список продуктів</h2>
    <ProductList />
  </div>
</template>

<script>
import ProductList from '../components/ProductList.vue';

export default {
  name: 'ManageReviews',
  components: {
    ProductList,
  },
};
</script>
