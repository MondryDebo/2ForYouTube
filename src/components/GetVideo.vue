<template>
  <div class="videoWrapper">
    <div class="innerWrapper">
      <h1 class="header">Download YouTube videos for free</h1>
      <p class="description">Best free tool to convert youtube video to MP3 or MP4!</p>
      <div class="getVideo">
        <input type="text" name="getVideo" placeholder="Paste YouTube link here" />
        <button type="button" class="search">Search<ion-icon name="arrow-forward-outline"></ion-icon></button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'GetVideo',
}
</script>

<style lang="scss" scoped>
  .videoWrapper {
    margin-top: 50px;
    border: 1px solid rgba(0, 0, 0, 0.1);
    width: 75%;
    height: auto;
    background: white;
    border-radius: 15px;
    box-shadow: 0 30px 30px -10px rgba(0, 0, 0, .3);
    padding: 50px;
  }

  .innerWrapper {
    text-align: center;
  }

  .getVideo {
    margin: 20px;
    display: flex;
    justify-content: center;

    input {
      width: 75%;
      height: 50px;
      padding: 8.5px 0 8.5px 40px;
      border-radius: 15px;
      border: 2px solid rgba(238, 238, 238, 0.562);
      background: url('../assets/search-outline.svg');
      background-repeat: no-repeat;
      background-size: 30px;
      background-position: 7.5px 7.5px;
    }

    button {
      display: flex;
      justify-content: center;
      align-items: center;
      margin-left: 20px;
      width: 100px;
      border: none;
      border-radius: 10px;
      background: rgba(238, 238, 238, 0.562);
      cursor: pointer;
    
      ion-icon {
        margin-left: 5px;
      }
    }
  }
</style>