<template>
  <div class="navbarWrapper">
    <div class="logo" title="2ForYouTube">
      <img src="../assets/logo.svg" width="50" height="50">
      <p>2ForYouTube</p>
    </div>
    <nav>
      <ul>
        <li><router-link to="/"><ion-icon name="home-outline"></ion-icon>Home</router-link></li>
        <li><router-link to="/about"><ion-icon name="information-circle-outline"></ion-icon>About</router-link></li>
      </ul>
    </nav>
  </div>
</template>

<script>
export default {
  name: 'Navbar',
}
</script>

<style lang="scss" scoped>
  .navbarWrapper {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 30px 10%;
    height: 110px;
    width: 100%;
    border-bottom: 1px solid rgba(0, 0, 0, 0.1);
  }

  .logo {
    display: flex;
    align-items: center;

    p {
      font-size: 25px;
      font-weight: 800;
      margin: 10px;
    }
  }

  li, a {
    font-weight: 600;
    font-size: 16px;
    color: black;
    text-decoration: none;
    padding: 20px;
    display: inline;

    &.router-link-exact-active {
      background-color: rgba(238, 238, 238, 0.562);
      border-radius: 5px;
    }

    ion-icon {
      transform: translate(-5px, 2.5px);
      font-size: 20px;
    }
  }
</style>