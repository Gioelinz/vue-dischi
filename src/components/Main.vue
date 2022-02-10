<template>
  <main>
    <div class="container">
      <div class="row row-cols-1 row-cols-md-3 row-cols-lg-5">
        <div class="col" v-for="disc in discs" :key="disc.title">
          {{ disc.author }}
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import axios from "axios";

export default {
  name: "Main",
  data() {
    return {
      discs: [],
    };
  },
  methods: {
    getApiDiscs() {
      axios
        .get("https://flynn.boolean.careers/exercises/api/array/music")
        .then((res) => {
          this.discs = res.data.response;
        });
    },
  },
  mounted() {
    this.getApiDiscs();
  },
};
</script>

<style lang="scss" scoped>
</style>
