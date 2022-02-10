<template>
  <header class="py-2 px-4">
    <img
      src="https://upload.wikimedia.org/wikipedia/commons/7/75/Spotify_icon.png"
      alt=""
    />
  </header>
</template>

<script>
export default {
  name: "Header",
};
</script>

<style lang="scss" scoped>
@import "../assets/scss/style.scss";
header {
  background-color: $primary_color;
  height: 70px;
  img {
    height: 50px;
  }
}
</style>