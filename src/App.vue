<template>
  <v-app>
    <ComingSoonPage />
  </v-app>
</template>

<script>
import ComingSoonPage from './components/ComingSoonPage.vue'

export default {
  name: 'App',
  components: {
    ComingSoonPage
  }
}
</script>

<style>

@font-face {
  font-family: "Franklin";
  src: local("Franklin"),
  url(./fonts/LibreFranklin-Regular.ttf) format("truetype");
}

#app {
  font-family: "Franklin", Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 5rem;
}
</style>
