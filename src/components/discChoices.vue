<template>
  <section>
    <div class="row" v-if="boolean">
      <div
        v-for="cd in musics"
        :key="cd"
        class="col-lg-3 col-md-5 col-sm-5 col-15 pt-5"
      >
        <div class="cd-container m-1">
          <img :src="cd.poster" class="pt-3 img-fluid" />
          <h6 class="p-2 text-uppercase">{{ cd.title }}</h6>
          <p class="pt-1">{{ cd.author }}</p>
          <p class="pb-2">{{ cd.year }}</p>
        </div>
      </div>
    </div>
    <div class="row" v-else>
      <div class="col-15 d-flex justify-content-center">
        <Loader msg="loading..." />
      </div>
    </div>
  </section>
</template>

<script>
import axios from "axios";
import Loader from "./Loader.vue";

export default {
  name: "discChoices",
  components: {
    Loader,
  },

  data() {
    return {
      musics: [],
      boolean: false,
    };
  },
  created() {
    setTimeout(() => {
      axios
        .get("https://flynn.boolean.careers/exercises/api/array/music")
        .then((response) => {
          this.musics = response.data.response.slice();
          this.boolean = true;
        });
    },1000);
  },
};
</script>

<style lang="scss" scoped>
@import "../style/variables.scss";

.cd-container {
  background-color: $back-ground;
  width: 70%;
  min-height: 320px;
  cursor: pointer;
}

img {
  width: 80%;
}

h6 {
  color: $title-color;
}

p {
  color: $subtitle-color;
}
</style>