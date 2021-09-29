<template>
  <div class="row">
    <div
      v-for="cd in musics"
      :key="cd"
      class="col-lg-3 col-md-4 col-sm-6 col-12 pt-5"
    >
      <div class="cd-container m-1">
        <img :src="cd.poster" class="pt-3 img-fluid" />
        <h5 class="p-2 text-uppercase">{{ cd.title }}</h5>
        <h6 class="pt-1">{{ cd.author }}</h6>
        <p class="pb-2">{{ cd.year }}</p>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "discChoices",

  data() {
    return {
      musics: [],
    };
  },
  created() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((response) => {
        this.musics = response.data.response.slice();
      });
  },
};
</script>

<style lang="scss" scoped>
@import "../style/variables.scss";

.cd-container {
  background-color: $back-ground;
  width: 70%;
  min-height: 350px;
  cursor: pointer;
}

img {
  width: 80%;
}

h5 {
  color: $title-color;
}

h6,
p {
  color: $subtitle-color;
}
</style>