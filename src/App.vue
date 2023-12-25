<template>
  <!-- <nav><router-link to="/">Home</router-link> |</nav> -->
  <Header />
  <router-view />
  <Footer />
</template>

<script>
import Header from '@/components/Header.vue';
import Footer from '@/components/Footer.vue';
export default {
  name: 'App',
  components: {
    Header,
    Footer,
  },
};
</script>

<style>
/* nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
} */
</style>
