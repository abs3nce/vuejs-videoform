<template>
  <div id="app">
    <video-form v-bind:videos="videos" @add:video="addVideo"/>
  </div>
</template>

<script>
import VideoForm from './components/VideoForm.vue'

export default {
  name: 'App',
  components: {
    VideoForm,
  },
  data() {
    return {
      videos: [
        {
          id: 1,
          videoName: "Top 3 Life Hacks",
          likes: 200000,
          subs: 300000,
        },
        {
          id: 2,
          videoName: "Cutting a person with 10000 degree knife",
          likes: 500000,
          subs: 1000000,
        },
        {
          id: 3,
          videoName: "lofi hip hop radio - beats to relax/study to",
          likes: 3100000,
          subs: 6730000,
        }
      ]
    }
  },
  methods: {
    addVideo(video) {
      console.log(video)
      this.videos.push({
        id: this.videos.length + 1,
        videoName: video.videoName,
        likes: video.likes,
        subs: video.subs,
      });
    }
  }
}
</script>

<style lang=scss>
:root {
  --color-text: #fff;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
}

body {
  background-color: #1b1b1b;
  color: var(--color-text);

  h1, input {
    color: var(--color-text);
  }
}
</style>
