<template>
  <div id="portfolio">
    <div class="container-fluid p-0">
      <div class="row no-gutters">
        <div class="col-lg-4 col-sm-6" v-for="song in songs" v-bind:key="song.id">
          <div class="portfolio-box" v-on:click="`/songs/${song.id}`">
            <img class="img-fluid" src="assets/img/portfolio/thumbnails/1.jpg" alt="..." />
            <div class="portfolio-box-caption">
              <div class="project-category text-white-50">{{ song.title }}</div>
              <div class="project-name">{{ song.description }}</div>
              <router-link class="song-info" v-bind:to="`/songs/${song.id}`">More Info</router-link>
              <!-- <div class="project-name">Project Name</div> -->
            </div>
          </div>
        </div>
      </div>
    </div>
    </div>
      <!-- <div v-for="song in songs" v-bind:key="song.id">
        <h3>{{ song.title }}</h3>
        <p>{{ song.description }}</p>
        <router-link v-bind:to="`/songs/${song.id}`">More Info</router-link>
        <br>
        <button v-on:click="createFavorites">Add to Favorites</button>
      </div> -->
</template>

<style>
.song-info {
  color: black;
}
</style>

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