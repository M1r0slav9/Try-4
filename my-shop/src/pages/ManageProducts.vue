<template>
  <div>
    <h2>Пошук товарів</h2>
    <input v-model="searchQuery" placeholder="Введіть назву товару" />
    <ManageCart />
    <ProductList :products="filteredProducts" />
  </div>
</template>

<script>
import { ref, computed, provide } from "vue";
import ProductList from "../components/ProductList.vue";
import ManageCart from "../components/ManageCart.vue";

export default {
  name: "ManageProducts",
  components: { ProductList, ManageCart },
  setup() {
    const searchQuery = ref("");
    const cartItems = ref([]);

    const products = ref([
      { id: 1, name: "Смартфон", description: "Сучасний смартфон", price: 1200, image: "https://img.freepik.com/free-photo/white-cell-phone-box-background_58702-4721.jpg" },
      { id: 2, name: "Ноутбук", description: "Потужний ноутбук", price: 2500, image: "https://img.freepik.com/free-photo/workplace-with-laptop-stand-near-eyeglasses_23-2148040478.jpg" },
      { id: 3, name: "Навушники", description: "Бездротові навушники", price: 300, image: "https://img.freepik.com/free-photo/closeup-shot-white-wireless-headphones-with-their-case-white-background_181624-31412.jpg" },
    ]);

    const filteredProducts = computed(() =>
      products.value.filter(product =>
        product.name.toLowerCase().includes(searchQuery.value.toLowerCase())
      )
    );

    const totalPrice = computed(() =>
      cartItems.value.reduce((sum, item) => sum + item.price, 0)
    );

    function addToCart(product) {
      cartItems.value.push(product);
    }

    function removeItem(index) {
      cartItems.value.splice(index, 1);
    }

    provide("cartItems", cartItems);
    provide("totalPrice", totalPrice);
    provide("addToCart", addToCart);
    provide("removeItem", removeItem);

    return {
      searchQuery,
      filteredProducts,
      cartItems,
      totalPrice,
      addToCart,
      removeItem,
    };
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
