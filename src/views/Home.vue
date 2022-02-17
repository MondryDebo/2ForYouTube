<template>
  <div class="home">
    <GetVideo />
  </div>
</template>

<script>
import GetVideo from '@/components/GetVideo.vue';

export default {
  name: 'Home',
  components: {
    GetVideo,
  }
}
</script>

<style lang="scss">
  .home {
    display: flex;
    justify-content: center;
  }
</style>
