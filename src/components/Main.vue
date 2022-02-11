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
        <div class="col" v-for="disc in filteredCards" :key="disc.title">
          <Loader v-if="isLoading" msg="Discs Loading..." />
          <DiscsCard
            v-else
            :author="disc.author"
            :poster="disc.poster"
            :title="disc.title"
            :year="disc.year"
          />
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import DiscsCard from "./DiscsCard.vue";
import Loader from "./Loader.vue";

export default {
  name: "Main",
  components: {
    DiscsCard,
    Loader,
  },
  props: ["isLoading", "discs", "filterGenre"],
  computed: {
    filteredCards() {
      const filter = this.filterGenre;
      return this.discs.filter((disc) => {
        if (disc.genre == filter || filter == "Tutti" || filter == "")
          return true;
      });
    },
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
