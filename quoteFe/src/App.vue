<template>
  <div id="app">
    <NavBar />
    <div class="content">
      <RandomQuote />
    </div>
  </div>
</template>

<script>
import NavBar from './components/NavBar.vue';
import RandomQuote from './components/randomQuote.vue';

export default {
  name: 'App',
  components: {
    NavBar,
    RandomQuote
  }
};
</script>

<style>
/* Add global styles as needed */
html, body, #app {
  height: 100%;
  margin: 0;
  font-family: "Georgia", serif;
  background-color: #f4f1ed;
  color: #3e3e3e;
}

.content {
  padding-top: 80px; /* Adds space to prevent overlap with navbar */
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
</style>
