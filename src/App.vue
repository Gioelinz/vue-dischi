<template>
  <div id="app">
    <Header :discs="discs" @filter-genre="test" />
    <Main :is-loading="isLoading" :discs="discs" :filter-genre="term" />
  </div>
</template>

<script>
import axios from "axios";

import Header from "./components/Header.vue";
import Main from "./components/Main.vue";

export default {
  name: "App",
  components: {
    Header,
    Main,
  },
  data() {
    return {
      isLoading: false,
      discs: [],
      term: "",
    };
  },
  methods: {
    getApiDiscs() {
      this.isLoading = true;
      axios
        .get("https://flynn.boolean.careers/exercises/api/array/music")
        .then((res) => {
          this.discs = res.data.response;
        })
        .finally(() => {
          this.isLoading = false;
        });
    },
    test(key) {
      this.term = key;
    },
  },
  mounted() {
    this.getApiDiscs();
  },
};
</script>

<style lang="scss">
@import "./assets/scss/style.scss";

body {
  background-color: $secondary_color;
}

img {
  max-width: 100%;
  pointer-events: none;
  user-select: none;
}
</style>
