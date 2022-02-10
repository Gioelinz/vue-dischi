<template>
  <main>
    <div class="container">
      <div
        class="
          row row-cols-1 row-cols-md-3 row-cols-lg-4 row-cols-xl-5
          gy-3
          gx-4
        "
      >
        <div class="col" v-for="disc in discs" :key="disc.title">
          <DiscsCard
            v-if="!isLoading"
            :author="disc.author"
            :poster="disc.poster"
            :title="disc.title"
            :year="disc.year"
          />
          <Loader v-else msg="Discs Loading..." />
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import axios from "axios";

import DiscsCard from "./DiscsCard.vue";
import Loader from "./Loader.vue";

export default {
  name: "Main",
  components: {
    DiscsCard,
    Loader,
  },
  data() {
    return {
      discs: [],
      isLoading: false,
    };
  },
  methods: {
    getApiDiscs() {
      this.isLoading = true;
      axios
        .get("https://flynn.boolean.careers/exercises/api/array/music")
        .then((res) => {
          this.discs = res.data.response;
          this.isLoading = false;
        });
    },
  },
  mounted() {
    this.getApiDiscs();
  },
};
</script>

<style lang="scss" scoped>
main {
  height: calc(100vh - 70px);
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  padding: 20px 0;
  overflow: auto;
}
</style>
