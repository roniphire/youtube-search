<template>
  <div id="app">
    <SearchBar @searchChange="onSearchChange"></SearchBar>
  </div>
</template>

<script>
import SearchBar from "./components/SearchBar.vue";

export default {
  name: "App",

  components: {
    SearchBar,
  },

  methods: {
    onSearchChange(searchTerm) {
      console.info(searchTerm);
    },
  },
};
</script>


