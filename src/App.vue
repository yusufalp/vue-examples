<template>
  <div>
    <SearchBar @searchTermChange="onSearchTermChange"></SearchBar>
    <VideoList :videos="videos"></VideoList>
  </div>
</template>

<script>
import SearchBar from "./components/SearchBar";
import VideoList from "./components/VideoList";
import axios from "axios";

const API_KEY = "AIzaSyA5_4Ur8GkVTTT9R7_gyUEbpq1n-CGenkQ";

export default {
  name: 'App',
  components: {
    SearchBar,
    VideoList
  },
  data: function() {
    return {
      videos: []
    }
  },
  methods: {
    onSearchTermChange: function(searchTerm) {
      axios.get("https://www.googleapis.com/youtube/v3/search", {
        params: {
          key: API_KEY,
          type: "video",
          part: "snippet",
          q: searchTerm
        }
      })
      .then(response => {
        this.videos = response.data.items;
      });
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  width: 80%;
  margin: 60px auto 0;
}
</style>
