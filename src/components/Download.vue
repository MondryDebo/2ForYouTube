<template>
  <div class="downloadWrapper">
    <img :src="thumbnail" :alt="title" width="350" class="thumbnail">
    <div class="right">
      <h3 class="title">{{ title }}</h3>
      <p class="author">{{ author }}</p>
      <p class="duration">{{ (convertIso8601(duration).hours ? (convertIso8601(duration).hours > 10 ? convertIso8601(duration).hours : '0' + convertIso8601(duration).hours) + ':' : '') + convertIso8601(duration).minutes + ':' + (convertIso8601(duration).seconds > 10 ? convertIso8601(duration).seconds : '0' + convertIso8601(duration).seconds) }}</p>
      <div class="download">
        <button class="downloadBtn">Download</button>
          <div class="dropdownWrapper">
            <select class="dropdown" name="resolution" v-model="selected">
              <option disabled value="">Please select one</option>
              <option v-for="resolution in options" v-bind:key="resolution.value" :value="resolution.value">{{ resolution.text }}</option>
            </select>
            <span class="customArrow"></span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { parse } from 'tinyduration';

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
      options: [
        { text: 'MP4 (1080p)', value: '1080' },
        { text: 'MP4 (720p)', value: '720' },
        { text: 'MP4 (480p)', value: '480' },
        { text: 'MP4 (360p)', value: '360' },
        { text: 'MP4 (240p)', value: '240' },
        { text: 'MP4 (144p)', value: '144' },
        { text: 'MP3 (128kbps)', value: 'mp3' },
      ],
      selected: '',
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
      }
    }

    .thumbnail {
      border-radius: 5px;
    }
  }
</style>
