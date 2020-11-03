<template>
  <div class="video-box">
    <div class="upload">
      <input id="videoName" type="text" v-model="videoName">
      <h1>{{ videoName || "Meno videa" }}</h1>
      <h1>Likes: {{ likes }}</h1>
      <h1>Odoberatelia: {{ subs }}</h1>
      <div class="buttons">
        <button v-on:click="like()">Like</button>
        <button v-on:click="subscribe()">Subscribe</button>
        <input id="videoSubmit" type="submit" @click.prevent="submit">
      </div>
    </div>

    <div class="list">
      <table>
        <tr>
          <th>Name</th>
          <th>Likes</th>
          <th>Subs</th>
        </tr>
        <tbody>
        <tr v-for="video in videos" :key="video.id">
          <td> {{ video.videoName }}</td>
          <td> {{ video.likes }}</td>
          <td> {{ video.subs }}</td>
        </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  name: 'VideoForm',
  props: {
    videos: Array,
  },
  data() {
    return {
      likes: 0,
      subs: 0,
      videoName: '',
    }
  },
  methods: {
    like() {
      this.likes++;
    },
    subscribe() {
      this.subs++;
    },
    submit() {
      this.$emit('add:video', {
        likes: this.likes,
        subs: this.subs,
        videoName: this.videoName,
      });
      this.likes = 0;
      this.subs = 0;
      this.videoName = '';
    }
  }
}
</script>

<style scoped>
.video-box {
  display: flex;
  justify-content: space-evenly
}

.upload {
  width: 40%;
  height: 100vh;
}

.buttons {
  width: 60%;
  margin: auto;
  display: flex;
  justify-content: space-evenly
}

.list {
  width: 40%;
  height: 100vh
}
</style>
