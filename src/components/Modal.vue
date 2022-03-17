<template>
  <div class="outerWrapper">
    <div class="innerWrapper">
      <p class="title">#{{ title }}</p>
      <div class="line"></div>
      <button @click="$router.go('/')"><ion-icon name="refresh-outline"></ion-icon> Download another video</button>
      <div class="downloadButton">
        <iframe class="iframe" style="width: 100%; border: 0px; overflow: hidden; font-size: 16px; font-weight: bold; height: 60px;" scrolling="no" :src="downloadBtn"></iframe>
      </div>
      <p>
        Thank you for using website. I'm student without
        any revenue. If you found any issues please contact
        on mail <a href="mailto:tymondebicki6@gmail.com" target="_blank">tymondebicki6@gmail.com</a>.
        Please if you can <a href="https://paypal.me/MondryDebo" target="_blank"><ion-icon name="logo-paypal"></ion-icon>Donate me</a> here.
      </p>
      <div class="downloadThumbnail">
        <a :href="thumbnail" download="2ForYouTube" target="_blank">
          <button>
            <ion-icon name="cloud-download-outline"></ion-icon> 
            Download Thumbnail
          </button>
        </a>
      </div>
      <div class="embed">
        <iframe width="auto" height="100%" :src="embed" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
      </div>
      <div class="line"></div>
      <div class="close">
        <button @click="$emit('close-modal')">Close</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Modal',
  props: {
    item: {
      type: Object,
      required: true,
    },
    resolution: {
      type: String,
      required: false,
    },
  },
  data() {
    return {
      thumbnail: null,
      title: null,
      downloadBtn: null,
      videoId: null,
      embed: null,
    };
  },
  mounted() {
    this.thumbnail = this.item.videoDetails.thumbnail;
    this.title = this.item.videoDetails.title;
    this.videoId = this.item.videoId;
    this.embed = `https://www.youtube.com/embed/${this.videoId}`;
    this.downloadBtn = this.resolution ? `https://loader.to/api/button/?url=${this.item.videoId}&f=${this.resolution}&color=64c896` : `https://loader.to/api/button/?url=${this.item.videoId}&f=1080&color=64c896`;
  },
}
</script>

<style lang="scss" scoped>
  .outerWrapper {
    display: flex;
    align-items: center;
    height: 100vh;
    width: 400px;
    position: fixed;
    top: 0;
    z-index: 1000000;
  }

  button {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 200px;
    padding: 10px;
    border: none;
    border-radius: 5px;
    background: #5f53ca;
    color: white;
    font-weight: 600;

    ion-icon {
      width: 20px;
      height: 20px;
      margin-right: 5px;
    }
  }

  .innerWrapper {
    background: #21252bf3;
    border-radius: 15px;
    width: 100%;
    height: auto;
    display: flex;
    padding: 30px;
    align-items: center;
    flex-direction: column;

    .title {
      margin: 0;
      text-align: left;
      font-size: 15px;
    }

    .line {
      margin: 10px;
    }

    .close {
      button {
        display: flex;
        justify-content: center;
        align-items: center;
        width: 200px;
        padding: 10px;
        border: none;
        border-radius: 5px;
        background: #5f53ca;
        color: white;
        font-weight: 600;
      }
    }

    .downloadButton {
      display: block;
      margin-top: 15px;
    }

    p {
      margin-top: 15px;
      color: white;

      a {
        color: yellow;
        font-weight: 600;
        text-decoration: none;

        &:hover {
          text-decoration: underline;
        }
      }
    }

    .downloadThumbnail {
      margin-top: 15px;

      button {
        display: flex;
        justify-content: center;
        align-items: center;
        width: 200px;
        padding: 10px;
        border: none;
        border-radius: 5px;
        background: #64c896;
        color: white;
        font-weight: 600;

        ion-icon {
          width: 20px;
          height: 20px;
          margin-right: 5px;
        }
      }
    }

    .embed {
      margin-top: 15px;

      iframe {
        border-radius: 5px;
      }
    }
  }
</style>