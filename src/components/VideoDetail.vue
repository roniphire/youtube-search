<template>
  <div v-if="video" class="col-md-8">
    <div class="embed-responsive embed-responsive-16by9">
      <iframe :src="videoUrl" frameborder="0" class="embed-responsive-item" />
    </div>
    <div class="details">
      <h5>{{ video.snippet.title }}</h5>
      <p>{{ video.snippet.desctiption }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "VideoDetail",

  props: ["video"],

  computed: {
    videoUrl() {
      const { videoId } = this.video.id;
      return `https://www.youtube.com/embed/${videoId}`;
    },
  },
};
</script>

<style scopped>
.details {
  margin-top: 10px;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 4px;
}
</style>