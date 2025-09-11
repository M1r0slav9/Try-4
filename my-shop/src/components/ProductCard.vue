<template>
  <div class="product-card">
    <img :src="image" :alt="name" />
    <h3>{{ name }}</h3>
    <p>{{ description }}</p>
    <p class="price">{{ price }} грн</p>
    <button @click="addToCartHandler">Додати в кошик</button>
  </div>
</template>

<script>
import { inject } from "vue";

export default {
  name: "ProductCard",
  props: {
    name: String,
    description: String,
    price: Number,
    image: String,
  },
  setup(props) {
    const addToCart = inject("addToCart");

    const addToCartHandler = () => {
      addToCart({
        name: props.name,
        description: props.description,
        price: props.price,
        image: props.image,
      });
    };

    return { addToCartHandler };
  },
};
</script>

<style scoped>
.product-card {
  border: 1px solid #ddd;
  padding: 15px;
  border-radius: 10px;
  text-align: center;
  width: 200px;
  background: #fff;
  box-shadow: 0 2px 5px rgba(0,0,0,0.1);
}
.product-card img {
  width: 100%;
  height: auto;
  border-radius: 8px;
}
.price {
  font-weight: bold;
  margin: 10px 0;
}
button {
  background-color: #42b983;
  color: white;
  border: none;
  padding: 8px 12px;
  border-radius: 6px;
  cursor: pointer;
  transition: background 0.3s;
}
button:hover {
  background-color: #369d6e;
}
</style>
