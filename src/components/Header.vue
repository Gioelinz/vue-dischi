<template>
  <header class="py-2 px-4">
    <img
      src="https://upload.wikimedia.org/wikipedia/commons/7/75/Spotify_icon.png"
      alt="Logo"
    />
    <div class="filters">
      <select id="filtergenre" @change="test" v-model="key">
        <option value="rock">Rock</option>
      </select>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      key: "",
    };
  },
  methods: {
    test() {
      console.log(event.target.value, this.key);
    },
    test1() {
      console.log("clicked");
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