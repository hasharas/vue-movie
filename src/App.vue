<template>
  <div id="app">
    <Header />
    <Hero />
    <Introduction />
    <MovieGrid />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Hero from "./components/Hero.vue";
import Introduction from "./components/Introduction.vue";
import MovieGrid from "./components/MovieGrid.vue";

export default {
  components: {
    Header,
    Hero,
    Introduction,
    MovieGrid,
  },
};
</script>
