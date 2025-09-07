<template>
  <div>
    <h2>Пошук товарів</h2>
    <input 
      v-model="searchQuery" 
      placeholder="Введіть назву товару"
    />
    <ProductList :products="filteredProducts" />
  </div>
</template>

<script>
import ProductList from '../components/ProductList.vue';

export default {
  components: { ProductList },
  data() {
    return {
      searchQuery: "",
      products: [
        { id: 1, name: 'Смартфон', description: 'Сучасний смартфон з великим екраном', price: 1200, image: 'https://via.placeholder.com/150' },
        { id: 2, name: 'Ноутбук', description: 'Легкий ноутбук для роботи та навчання', price: 2500, image: 'https://via.placeholder.com/150' },
        { id: 3, name: 'Навушники', description: 'Бездротові навушники з якісним звуком', price: 300, image: 'https://via.placeholder.com/150' },
      ],
    };
  },
  computed: {
    filteredProducts() {
      return this.products.filter(product =>
        product.name.toLowerCase().includes(this.searchQuery.toLowerCase())
      );
    },
  },
};
</script>

<style scoped>
h2 {
  text-align: center;
  margin-bottom: 10px;
}
input {
  display: block;
  margin: 0 auto 20px auto;
  padding: 5px 10px;
  width: 300px;
}
</style>
