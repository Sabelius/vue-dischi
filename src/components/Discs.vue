<template>
  <section>
    <div class="container">
      <discChoices />
    </div>
  </section>
</template>

<script>
import discChoices from "./discChoices.vue";

export default {
  name: "Discs",

  components: {
    discChoices,
  },

};
</script>

<style lang="scss" scoped>
@import "../style/variables.scss";
</style>
