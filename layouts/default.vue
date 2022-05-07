<template>
  <v-app>
    <TheHeader />
    <Nuxt />
    <TheFooter />
  </v-app>
</template>

<script>
import TheHeader from "../components/TheHeader.vue";
import TheFooter from "../components/TheFooter.vue";

export default {
  name: 'DefaultLayout',
  components: { TheHeader, TheFooter },
  data() {
    return {
      
    }
  },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@100;200;300;400;500;600;700;800;900&family=Roboto:wght@100;300;400;500;700;900&display=swap');
* { padding: 0; margin: 0; box-sizing: inherit; }
body { font-size: 16px; box-sizing: border-box; background: #F5F6F8; }
ul { list-style-type: none; }
a { text-decoration: none; }
</style>
