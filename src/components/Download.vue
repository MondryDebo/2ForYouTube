<template>
  <div class="downloadWrapper">
    <img :src="thumbnail" :alt="title" width="350" class="thumbnail">
    <div class="right">
      <h3 class="title">{{ title }}</h3>
      <p class="author">{{ author }}</p>
      <div class="download">
        <button class="downloadBtn">Download</button>
        <select>
          <option value="1080">MP4 (1080p)</option>
          <option value="360">MP4 (720p)</option>
          <option value="360">MP4 (480p)</option>
          <option value="360">MP4 (360p)</option>
          <option value="240">MP4 (240p)</option>
          <option value="144">MP4 (144p)</option>
          <option value="128">MP3 (128kbps)</option>
        </select>
      </div>
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
    },
    search: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      thumbnail: null,
      title: null,
      author: null,
      duration: null,
    };
  },
  mounted() {
    this.thumbnail = this.results.videoDetails.thumbnail;
    this.title = this.results.videoDetails.title;
    this.author = this.results.videoDetails.author;
    this.duration = this.results.videoDetails.duration;
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
  
      .download {
        margin-top: 15px;
        display: flex;

        .downloadBtn {
          display: flex;
          justify-content: center;
          align-items: center;
          width: 150px;
          padding: 10px;
          border: none;
          border-radius: 5px;
          background: rgb(34, 151, 5);
          color: white;
        }

        select {
          margin-left: 15px;
        }
      }
    }

    .thumbnail {
      border-radius: 5px;
    }
  }
</style>
