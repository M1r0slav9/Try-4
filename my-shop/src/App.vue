<template>
  <div id="app">
    <router-view></router-view>
    <FooterComponent />
  </div>
</template>

<script>
import FooterComponent from './components/FooterComponent.vue';

export default {
  name: 'App',
  components: {
    FooterComponent,
  },
};
</script>

<style>
#app {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

#app > router-view {
  flex: 1;
}
</style>