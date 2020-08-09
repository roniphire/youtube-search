<template>
  <li class="list-group-item" @click="onSelectVideo">
    <img class="mr-3" :src="thumbnailUri" />
    <div class="media-body">
      {{ video.snippet.title }}
    </div>
  </li>
</template>

<script>
export default {
  name: 'VideoListItem',

  props: {
    video: Object,
  },

  computed: {
    thumbnailUri() {
      return this.video.snippet.thumbnails.default.url;
    },
  },

  methods: {
    onSelectVideo() {
      this.$emit('selectVideo', this.video);
    },
  },
};
</script>

<style scoped>
li {
  display: flex;
}

li:hover {
  background-color: #fafa;
}
</style>
