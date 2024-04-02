<script>
import AppHeader from './components/AppHeader.vue';
export default {
  name: 'Boolfolio',
  components: { AppHeader }
};
</script>

<template>
  <AppHeader />
  <main class="container pt-4">
    <RouterView />
  </main>
</template>

<style scoped></style>
