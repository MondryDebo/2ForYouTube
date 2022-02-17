<template>
  <div id="app">
    <div class="header">
      <div class="logo">
        <img src="./assets/logo.svg" width="50" height="50">
        <p>2ForYouTube</p>
      </div>
      <nav>
        <ul>
          <li class="active"><router-link to="/"><ion-icon name="home-outline"></ion-icon>Home</router-link></li>
          <li><router-link to="/"><ion-icon name="musical-notes-outline"></ion-icon>YouTube to MP3</router-link></li>
          <li><router-link to="/"><ion-icon name="videocam-outline"></ion-icon>YouTube to MP4</router-link></li>
          <li><router-link to="/about"><ion-icon name="information-circle-outline"></ion-icon>About</router-link></li>
        </ul>
      </nav>
    </div>
    <router-view/>
  </div>
</template>

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

  .header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 30px 10%;
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
    padding: 15px;
    display: inline;

    &.active {
      background-color: rgba(238, 238, 238, 0.562);
      border-radius: 5px;
    }

    ion-icon {
      transform: translate(-5px, 2.5px);
      font-size: 20px;
    }
  }
</style>