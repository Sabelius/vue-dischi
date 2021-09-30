<template>
  <section class="pt-4 col-15">
    <label>Choose an artist: </label>
    <select
      v-model.trim="selectedArtist"
      @change="$emit('search', selectedArtist)" 
    >
      >)
      <option v-for="author in artists" :key="author" :value="author">
        {{ author }}
      </option>
    </select>
  </section>
</template>

<script>
export default {
  name: "selectArtist",
  props: ["artists"],
  data() {
    return {
      selectedArtist: " ",
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