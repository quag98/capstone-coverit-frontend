<template>
  <div class="home">
    <div>
      <div v-for="song in songs" v-bind:key="song.id">
        <h3>{{ song.title }}</h3>
        <p>{{ song.description }}</p>
        <router-link v-bind:to="`/songs/${song.id}`">More Info</router-link>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      songs: [],
    };
  },
  created: function () {
    this.indexSongs();
  },
  methods: {
    indexSongs: function () {
      axios.get("/api/songs").then((response) => {
        this.songs = response.data;
        console.log("all songs:", this.songs);
      });
    },
  },
};
</script>