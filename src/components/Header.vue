<template>
  <header class="py-2 px-4">
    <img
      src="https://upload.wikimedia.org/wikipedia/commons/7/75/Spotify_icon.png"
      alt="Logo"
    />
    <div class="filters">
      <label class="me-2 text-black fs-6" for="filtergenre"
        >Seleziona genere:</label
      >
      <select
        id="filtergenre"
        @change="$emit('filter-genre', key)"
        v-model="key"
        :value="key"
      >
        <option value="Tutti">Tutti</option>
        <option
          v-for="(genre, index) in noDoubleGenre()"
          :key="index"
          :value="genre"
        >
          {{ genre }}
        </option>
      </select>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header",
  props: ["discs"],

  data() {
    return {
      key: "Tutti",
    };
  },
  methods: {
    noDoubleGenre() {
      const genres = [];
      this.discs.forEach((d) => {
        if (!genres.includes(d.genre)) genres.push(d.genre);
      });
      return genres;
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../assets/scss/style.scss";
header {
  background-color: $primary_color;
  height: 70px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  img {
    height: 50px;
  }
  #filtergenre {
    width: 100px;
    padding: 5px;
    border-radius: 10px;
    background-color: dodgerblue;
  }
}
</style>