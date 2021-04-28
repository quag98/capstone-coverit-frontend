<template>
  <div class="songs-show">
    <div>
      <h2>{{ song.title }}</h2>
      <p>{{ song.description }}</p>
      <p>{{ song.audio_link }}</p>
      <!-- <li>
        <ol> <router-link v-bind:t="`/songs/${song.id}/edit`"</ol>
      </li> -->
      <!-- <div v-for="song in songs" v-bind:key="song.id">
        <h3>{{ song.title }}</h3>
        <p>{{ song.description }}</p>
        <p>{{ song.audio_link }}</p>
      </div> -->
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      song: {},
    };
  },
  created: function () {
    this.showSongs();
  },
  methods: {
    showSongs: function () {
      axios.get("/api/songs/" + this.$route.params.id).then((response) => {
        console.log("songs show", response);
        this.song = response.data;
      });
    },
  },
};
</script>