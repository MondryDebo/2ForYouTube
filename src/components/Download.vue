<template>
  <div class="downloadWrapper">
    <img :src="thumbnail" :alt="title" width="350" class="thumbnail">
    <div class="right">
      <h3 class="title">{{ title }}</h3>
      <p class="author">{{ author }}</p>
      <p class="duration">{{ (convertIso8601(duration).hours ? (convertIso8601(duration).hours > 10 ? convertIso8601(duration).hours : '0' + convertIso8601(duration).hours) + ':' : '') + convertIso8601(duration).minutes + ':' + (convertIso8601(duration).seconds > 10 ? convertIso8601(duration).seconds : '0' + convertIso8601(duration).seconds) }}</p>
      <div class="download">
        <button class="downloadBtn">Download</button>
        <Dropdown />
      </div>
    </div>
  </div>
</template>

<script>
import Dropdown from '@/components/Dropdown.vue';
import { parse } from 'tinyduration';

export default {
  name: 'Download',
  components: {
    Dropdown,
  },
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
  methods: {
    convertIso8601(duration) {
      return parse(duration);
    }
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

      .duration {
        margin-top: 5px;
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
          background: rgb(0, 128, 187);
          color: white;
        }
      }
    }

    .thumbnail {
      border-radius: 5px;
    }
  }
</style>
