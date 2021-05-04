<template>
  <div class="songs-show">
    <div>
      <h2>{{ song.title }}</h2>
      <p>{{ song.description }}</p>
      <iframe width="420" height="315" src="https://www.youtube.com/embed/yQORL_z-UsA?controls=0">
      </iframe>
      <br>
      <button v-on:click="createFavorites">Add to Favorites</button>
      <!-- <video width="320" height="240" controls>
        <source :src="song.audio_link" type="video/webm">
      </video> -->
      <!-- <p>{{ song.audio_link }}</p> -->
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