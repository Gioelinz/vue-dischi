<template>
  <div class="card-disc text-center" role="button">
    <img :src="poster" :alt="author" />
    <h4 class="text-white mt-3">{{ title.toUpperCase() }}</h4>
    <p class="text-secondary m-0 pt-2">{{ author }}</p>
    <p class="text-secondary">{{ year }}</p>
  </div>
</template>

<script>
export default {
  name: "DiscsCard",
  props: ["author", "poster", "title", "year"],
};
</script>

<style scoped lang="scss">
@import "../assets/scss/style.scss";

.card-disc {
  background-color: $primary_color;
  font-weight: bold;
  height: 400px;
  padding: 1.2rem;
}
</style>