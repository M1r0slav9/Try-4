<template>
  <div>
    <h2>Список відгуків</h2>
    <ReviewsComponent />
  </div>
</template>

<script>
import ReviewsComponent from '@/components/ReviewsComponent.vue';

export default {
  name: 'ManageProducts',
  components: {
    ReviewsComponent,
  },
};
</script>

