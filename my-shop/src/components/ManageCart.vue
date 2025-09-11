<template>
  <div class="cart">
    <h3>Кошик</h3>
    <div v-if="cartItems.length === 0">Кошик порожній</div>
    <ul>
      <li v-for="(item, index) in cartItems" :key="index">
        {{ item.name }} - {{ item.price }} грн
        <button @click="removeItem(index)">Видалити</button>
      </li>
    </ul>
    <p v-if="cartItems.length > 0">Загальна сума: {{ totalPrice }} грн</p>
  </div>
</template>

<script>
import { inject } from "vue";

export default {
  name: "ManageCart",
  setup() {
    const cartItems = inject("cartItems");
    const totalPrice = inject("totalPrice");
    const removeItem = inject("removeItem");

    return { cartItems, totalPrice, removeItem };
  },
};
</script>

<style scoped>
.cart {
  border: 1px solid #ddd;
  padding: 15px;
  border-radius: 10px;
  margin: 20px auto;
  max-width: 300px;
  background: #f9f9f9;
}
button {
  margin-left: 10px;
  background-color: #e74c3c;
  color: white;
  border: none;
  padding: 4px 8px;
  border-radius: 4px;
  cursor: pointer;
}
button:hover {
  background-color: #c0392b;
}
</style>
