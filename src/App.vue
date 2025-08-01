<template>
  <div id="app">
    <Header />
    <Hero />
    <Introduction />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Hero from "./components/Hero.vue";
import Introduction from "./components/Introduction.vue";

export default {
  components: {
    Header,
    Hero,
    Introduction,
  },
};
</script>
