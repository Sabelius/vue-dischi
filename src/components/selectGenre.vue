<template>
  <section class="pt-4 col-15">
      <label>Choose a genre: </label>
    <select
      v-model.trim="selectedGenre"
      @change="$emit('search', selectedGenre)"
    >
      >
      <option v-for="genre in genres" :key="genre" :value="genre">
        {{ genre }}
      </option>
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
label{
    color: $title-color;
    padding-right: 10px;
}
</style>