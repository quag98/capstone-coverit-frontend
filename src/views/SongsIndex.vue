<template>
  <div class="home">
    <div>
      <div v-for="song in songs" v-bind:key="song.id">
        <h3>{{ song.title }}</h3>
        <p>{{ song.description }}</p>
        <router-link v-bind:to="`/songs/${song.id}`">More Info</router-link>
        <br>
        <button v-on:click="createFavorites">Add to Favorites</button>
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
      title: "",
      description: "",
      // audio_link: "",
      song_id: "",
      artist_id: "",
      errors: [],
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
    createFavorites: function () {
      console.log("adding favorite:");
      var params = {
        song_id: this.title,
        artist_id: this.description,
        // audio_link: this.audio_link,
      };
      axios
      .post("/api/favorites", params)
      .then(() => {
        this.$router.push("/favorites");
      })
      .catch((error) => console.log(error.response));
    },
  },
};
</script>