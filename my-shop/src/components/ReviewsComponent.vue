<template>
  <table>
    <thead>
      <tr>
        <th>Ім'я користувача</th>
        <th>Оцінка</th>
        <th>Коментар</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(review, index) in reviews" :key="index">
        <td>{{ review.username }}</td>
        <td>{{ review.rating }}</td>
        <td>{{ review.comment }}</td>
      </tr>
    </tbody>
  </table>
</template>

<script>
import Papa from 'papaparse';

export default {
  name: 'ReviewsComponent',
  data() {
    return {
      reviews: [],
    };
  },
  created() {
    const csvContent = `
username,rating,comment
Олексій,5,Чудовий товар!
Марія,4,Все сподобалося, але доставка довга.
Іван,3,Я очікував кращу якість.
`;

    Papa.parse(csvContent.trim(), {
      header: true,
      complete: (result) => {
        this.reviews = result.data;
      },
    });
  },
};
</script>

<style scoped>
table {
  width: 90%;
  margin: 20px auto;
  border-collapse: collapse;
}

th, td {
  padding: 4px;
  background-color: #f8f9fa;
  border: 1px solid #ccc;
  text-align: left;
}

thead th {
  text-align: center;
}
</style>
