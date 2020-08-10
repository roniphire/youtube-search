<template>
  <div id="app" class="container">
    <SearchBar @searchChange="onSearchChange"></SearchBar>
    <div class="row">
      <VideoDetail :video="selectedVideo"></VideoDetail>
      <VideoList @selectVideo="onSelectVideo" :videos="videos"></VideoList>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import SearchBar from "./components/SearchBar.vue";
import VideoList from "./components/VideoList.vue";
import VideoDetail from "./components/VideoDetail.vue";

const API_KEY = "GENERATE";

export default {
  name: "App",

  components: {
    SearchBar,
    VideoList,
    VideoDetail,
  },

  data() {
    return {
      videos: [],
      selectedVideo: null,
    };
  },

  methods: {
    onSearchChange(searchTerm) {
      axios
        .get("https://www.googleapis.com/youtube/v3/search", {
          params: {
            key: API_KEY,
            type: "video",
            part: "snippet",
            q: searchTerm,
          },
        })
        .then((res) => {
          this.videos = res.data.items;
        });
    },

    onSelectVideo(video) {
      this.selectedVideo = video;
    },
  },
};
</script>
