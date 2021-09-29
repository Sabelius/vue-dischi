<template>
    <div class="row">
      <div
        v-for="cd in musics"
        :key="cd"
        class="col-lg-3 col-md-4 col-sm-6 col-12 pt-5"
      >
        <div class="cd-container m-1">
          <img :src="cd.poster" class="pt-3 img-fluid" />
          <h4 class="p-2">{{ cd.title }}</h4>
          <h5 class="pt-1">{{ cd.author }}</h5>
          <h6 class="pb-2">{{ cd.year }}</h6>
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

}
</script>

<style lang="scss" scoped>
@import "../style/variables.scss";

.cd-container {
  background-color: $back-ground;
  width: 60%;
  height: 350px;
  cursor: pointer;
}

img {
  width: 80%;
}

h4 {
  color: $title-color;
}

h5,
h6 {
  color: $subtitle-color;
}
</style>