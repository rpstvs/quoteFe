<template>
  <div id="app">
    <NavBar />
    <div class="content">
      <RandomQuote />
  
    </div>
    <div class="desc">
      <AuthorDescription />
    </div>
  </div>
</template>

<script>
import NavBar from './components/NavBar.vue';
import RandomQuote from './components/RandomQuote.vue';
import AuthorDescription from './components/AuthorDescription.vue';


export default {
  name: 'App',
  components: {
    NavBar,
    RandomQuote,
    AuthorDescription
  }
};
</script>

<style>
/* Add global styles as needed */
html, body, #app {
  height: 100%;
  margin: 0;
  font-family: "Georgia", serif;
  background-color: #FDF7E9;
  color: #3e3e3e;
  display: flex;
  flex-direction: column;
  
}

.content {
  padding-top: 150px; /* Adds space to prevent overlap with navbar */
  align-self: center;
}

.desc {
  padding-top: 30px; /* Adds space to prevent overlap with navbar */
 
  align-self: center;
  max-width: auto;
  max-height: auto;
  
}
</style>
