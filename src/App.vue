<template>
  <div id="app">
    <HeroImage />
    <Navbar />
    <router-view/>
  </div>
</template>

<script>
import Navbar from '@/components/Navbar.vue';
import HeroImage from '@/components/HeroImage.vue';

export default {
  name: 'App',
  components: {
    Navbar,
    HeroImage,
  }
}
</script>

<style lang="scss">
  @import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;600;800&display=swap');
  
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  body {
    font-family: 'Montserrat', sans-serif;
  }

  button {
    cursor: pointer;
  }

  a {
    text-decoration: none;
  }

  .line {
    width: 100%;
    height: 1px;
    background-color: rgb(207, 207, 207);
  }
</style>