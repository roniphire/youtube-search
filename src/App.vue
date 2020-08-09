<template>
  <div id="app" class="container">
    <SearchBar @searchChange="onSearchChange"></SearchBar>
    <VideoList @selectVideo="onSelectVideo" :videos="videos"></VideoList>
  </div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar.vue';
import VideoList from './components/VideoList.vue';
const API_KEY = 'AIzaSyBzQgSbtgpfzD8PPqFCgZbg-vt31Nu3LyA';

export default {
  name: 'App',

  components: {
    SearchBar,
    VideoList,
  },

  data() {
    return {
      videos: [],
    };
  },

  methods: {
    onSearchChange(searchTerm) {
      axios
        .get('https://www.googleapis.com/youtube/v3/search', {
          params: {
            key: API_KEY,
            type: 'video',
            part: 'snippet',
            q: searchTerm,
          },
        })
        .then((res) => {
          this.videos = res.data.items;
        });
    },

    onSelectVideo(video) {
      console.info(video);
    },
  },
};
</script>
