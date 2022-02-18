<template>
  <div class="downloadWrapper">
    <img :src="thumbnail" :alt="title" width="350" class="thumbnail">
    <div class="right">
      <h3 class="title">{{ title }}</h3>
      <p class="author">{{ author }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Download',
  props: {
    results: {
      type: Object,
      required: true,
    }
  },
  data() {
    return {
      thumbnail: null,
      title: null,
      author: null,
    };
  },
  mounted() {
    this.thumbnail = this.results.videoDetails.thumbnail;
    this.title = this.results.videoDetails.title;
    this.author = this.results.videoDetails.author;
  },
}
</script>

<style lang="scss" scoped>
  .downloadWrapper {
    display: flex;
    width: 350px;

    .right {
      display: flex;
      flex-direction: column;
      text-align: left;
      margin-left: 15px;

      .title {
        width: 550px;
        color: black;
        font-weight: 600;
      }
    }

    .thumbnail {
      border-radius: 5px;
    }
  }
</style>