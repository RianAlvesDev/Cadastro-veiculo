<template>
  <header>
    <NavBar :logo="carro_src" :alt="name" />
    <Router-View />
    <Footer />
  </header>
</template>

<script>
import NavBar from './components/NavBar.vue';
import Footer from './components/Footer.vue';

export default {
  components: {
    NavBar,
    Footer
  },
  data() {
    return{
      carro_src: "/public/img/logo.png",
      name: "carro"
    }
  }
}
</script>

<style scoped>
  * {
    font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
    padding: 0;
    margin: 0;
    box-sizing: border-box;
    background-color:rgb(248, 240, 227);
  }

  h1 {
    text-align: center;
    font-size: 42px;
    margin-bottom: 32px;
    color: #222;
  }
</style>
