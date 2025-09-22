<template>
  <div class="comments">
    <h2>Коментарі</h2>

    <!-- Фільтр за рейтингом -->
    <label for="ratingFilter">Фільтрувати за рейтингом:</label>
    <select id="ratingFilter" v-model="selectedRating">
      <option value="">Всі</option>
      <option value="5">5 зірок</option>
      <option value="4">4 зірки</option>
      <option value="3">3 зірки</option>
      <option value="2">2 зірки</option>
      <option value="1">1 зірка</option>
    </select>

    <!-- Відображення відфільтрованих коментарів -->
    <ul>
      <li v-for="(comment, index) in filteredReviews" :key="index">
        <strong>{{ comment.author }}</strong> — 
        <span>{{ comment.rating }}⭐</span>
        <p>{{ comment.text }}</p>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "CommentsList",
  data() {
    return {
      selectedRating: "", // для select
      comments: [
        { author: "Іван", rating: 5, text: "Дуже сподобалось!" },
        { author: "Марія", rating: 4, text: "Все добре, але можна краще." },
        { author: "Олег", rating: 3, text: "Посередньо." },
        { author: "Анна", rating: 2, text: "Не сподобалось." },
        { author: "Петро", rating: 1, text: "Жахливо!" }
      ]
    };
  },
  computed: {
    filteredReviews() {
      if (this.selectedRating) {
        return this.comments.filter(
          c => c.rating === Number(this.selectedRating)
        );
      }
      return this.comments; // якщо не вибрано фільтр → показати всі
    }
  }
};
</script>

<style scoped>
.comments {
  max-width: 500px;
  margin: auto;
}
.comments select {
  margin: 10px 0;
  padding: 5px;
}
.comments ul {
  list-style: none;
  padding: 0;
}
.comments li {
  border-bottom: 1px solid #ddd;
  padding: 10px 0;
}
</style>
