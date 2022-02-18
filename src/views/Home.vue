<template>
  <div class="home">
    <div class="videoWrapper">
      <div class="innerWrapper">
        <h1 class="header">Download YouTube videos for free</h1>
        <p class="description">Best free tool to convert youtube video to MP3 or MP4!</p>
        <div class="getVideo">
          <SearchInput v-model="searchValue" />
          <SearchButton @search="handleSearch" />
        </div>
        <div class="results" v-if="results.loaded && !loading">
          <Download :results="results" />
        </div>
        <div class="loader" v-if="loading"><div></div><div></div><div></div><div></div></div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import SearchInput from '@/components/SearchInput.vue';
import SearchButton from '@/components/SearchButton.vue';
import Download from '@/components/Download.vue';

export default {
  name: 'Home',
  components: {
    SearchInput,
    SearchButton,
    Download,
  },
  data() {
    return {
      loading: false,
      searchValue: '',
      results: {
        loaded: false,
        videoDetails: {
          title: '',
          thumbnail: '',
          author: '',
        }
      },
    };
  },
  methods: {
    async handleSearch() {
      this.loading = true;
      await axios.get(`https://youtube-api-nodejs.herokuapp.com/apiVideo?URL=${this.searchValue}`)
        .then(res => {
          this.results.loaded = true;
          this.loading = false;
          const data = res.data;
          console.log(data);
          this.results.videoDetails.title = data.videoDetails.title;
          this.results.videoDetails.thumbnail = data.videoDetails.thumbnails[4].url;
          this.results.videoDetails.author = data.videoDetails.author.name;
        })
        .catch(err => console.error(err));
    },
  },
}
</script>

<style lang="scss">
  .home {
    display: flex;
    justify-content: center;
  }

  .videoWrapper {
    margin: 50px;
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
  }

  .results {
    display: flex;
    margin-top: 25px;
    width: 95%;
    background: rgba(238, 238, 238, 0.562);
    padding: 20px;
    border-radius: 15px;
  }

  .loader {
    display: inline-block;
    position: relative;
    width: 64px;
    height: 64px;
    margin-top: 50px;
    @media (min-width: 768px) {
      width: 90px;
      height: 90px;
    }
  }
  .loader div {
    box-sizing: border-box;
    display: block;
    position: absolute;
    width: 64px;
    height: 64px;
    margin: 8px;
    border: 8px solid #1e3d4a;
    border-radius: 50%;
    animation: loader 1.2s cubic-bezier(0.5, 0, 0.5, 1) infinite;
    border-color: #1e3d4a transparent transparent transparent;
  }
  .loader div:nth-child(1) {
    animation-delay: -0.45s;
  }
  .loader div:nth-child(2) {
    animation-delay: -0.3s;
  }
  .loader div:nth-child(3) {
    animation-delay: -0.15s;
  }
  @keyframes loader {
    0% {
      transform: rotate(0deg);
    }
    100% {
      transform: rotate(360deg);
    }
  }
</style>
