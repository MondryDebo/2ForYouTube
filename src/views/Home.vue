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
        <div class="results" v-if="!loading">
          <p class="title">{{ results.videoDetails.title }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import SearchInput from '@/components/SearchInput.vue';
import SearchButton from '@/components/SearchButton.vue';

export default {
  name: 'Home',
  components: {
    SearchInput,
    SearchButton,
  },
  data() {
    return {
      loading: false,
      searchValue: '',
      results: {
        videoDetails: {
          title: '',
        }
      },
    };
  },
  methods: {
    async handleSearch() {
      const res = await axios.get(`https://youtube-api-nodejs.herokuapp.com/apiVideo?URL=${this.searchValue}`);
      const data = res.data;
      this.results.videoDetails.title = data.videoDetails.title;
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
  }
</style>
