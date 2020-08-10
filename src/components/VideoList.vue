<template>
  <ul class="list-group col-md-4">
    <VideoListItem
      v-for="video in videos"
      :key="video.etag"
      :video="video"
      @selectVideo="onSelectVideo"
    ></VideoListItem>
  </ul>
</template>

<script>
import VideoListItem from "./VideoListItem.vue";
export default {
  name: "VideoList",

  props: {
    videos: Array,
  },

  components: {
    VideoListItem,
  },

  methods: {
    onSelectVideo(video) {
      this.$emit("selectVideo", video);
    },
  },
};
</script>

<style scoped></style>
