<template>
  <div class="dropdownWrapper">
    <select class="dropdown" name="resolution">
      <option v-for="resolution in options" v-bind:key="resolution.value">{{ resolution.text }}</option>
    </select>
    <span class="customArrow"></span>
  </div>
</template>

<script>
export default {
  name: 'Dropdown',
  data() {
    return {
      options: [
        { text: 'MP4 (1080p)', value: '1080' },
        { text: 'MP4 (720p)', value: '720' },
        { text: 'MP4 (480p)', value: '480' },
        { text: 'MP4 (360p)', value: '360' },
        { text: 'MP4 (240p)', value: '240' },
        { text: 'MP4 (144p)', value: '144' },
        { text: 'MP3 (128kbps)', value: 'mp3' },
      ]
    };
  },
}
</script>

<style lang="scss" scoped>
.dropdownWrapper {
  position: relative;
  height: 37.5px;
  width: 200px;

  .dropdown {
    margin-left: 15px;
    height: 100%;
    width: 100%;
    border-radius: 5px;
    border: none;
    font-size: 1rem;
    padding: 10px;
    appearance: none;
  }

  .customArrow {
    position: absolute;
    width: 15px;
    top: 0;
    right: 0;
    display: block;
    height: 100%;
    pointer-events: none;

    &::before {
      content: '';
      position: absolute;
      top: 10px;
      right: 5px;
      height: 8px;
      width: 8px;
      border: 2px solid #333;
      border-top: 2px solid #fff;
      border-right: 2px solid #fff;
      transform: rotate(-45deg);
      transition: 0.5s;
    }
  }
}
</style>