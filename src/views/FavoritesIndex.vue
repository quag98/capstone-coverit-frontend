<template>
  <div class="home">
    <div>
      <div v-for="favorite in favorites" v-bind:key="favorite.id">
        <h3>{{ favorite.song_id }} </h3>
        <p>{{ favorite.artist_id }} </p>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      favorites: [],
    };
  },
  created: function () {
    this.indexFavorites();
  },
  methods: {
    indexFavorites: function () {
      axios.get("/api/favorites").then((response) => {
        this.favorites = response.data;
        console.log("user favorites", this.favorites);
      });
    },
  },
};
</script>