<template>
  <section class="pt-2">
    <select
      v-model.trim="selectedGenre"
      @change="$emit('search', selectedGenre)">
    >
      <option value=''>All genres</option>
      <option v-for="genre in genres" :key="genre" :value="genre">{{ genre }}</option>
    </select>
  </section>
</template>

<script>
export default {
  name: "selectGenre",
  props: ["genres"],
  data() {
    return {
      selectedGenre: " ",
    };
  },
};
</script>

<style lang="scss" scoped>
@import "../style/variables.scss";

select {
  width: 200px;
}
</style>