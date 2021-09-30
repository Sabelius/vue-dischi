<template>
  <section>
    <div class="row" v-if="boolean">
      <selectGenre :genres="genres" @search="genreSearch" />
      <h6 class="pt-4 col-15">Or</h6>
      <selectArtist :artists="artists" @search="artistSearch" />
      <div
        v-for="cd in filterGenreDiscs"
        :key="cd.title"
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
import selectGenre from "./selectGenre.vue";
import selectArtist from "./selectArtist.vue";

export default {
  name: "discChoices",
  components: {
    Loader,
    selectGenre,
    selectArtist,
  },

  data() {
    return {
      musics: [],
      genres: [],
      artists: [],
      boolean: false,
      selectedGenre: "",
      selectedArtist: "",
    };
  },

  computed: {
    filterGenreDiscs() {
      let newDiscList = [];
      if ((this.selectedGenre == "") && (this.selectedArtist == "")) {
        newDiscList = this.musics;
      } else if (this.genres.includes(this.selectedGenre)) {
        newDiscList = this.musics.filter(
          (element) => element.genre == this.selectedGenre
        );
      } else if (this.artists.includes(this.selectedArtist)) {
        newDiscList = this.musics.filter(
          (element) => element.author == this.selectedArtist
        );
      }
      return newDiscList;
    },
  },

  methods: {
    genreSearch(genre) {
      this.selectedGenre = genre;
    },
    artistSearch(author) {
      this.selectedArtist = author;
    },
  },

  created() {
    setTimeout(() => {
      axios
        .get("https://flynn.boolean.careers/exercises/api/array/music")
        .then((response) => {
          this.musics = response.data.response.slice();
          this.boolean = true;

          this.musics.forEach((element) => {
            if (!this.genres.includes(element.genre))
              this.genres.push(element.genre);
          });

          this.musics.forEach((element) => {
            if (!this.artists.includes(element.author))
              this.artists.push(element.author);
          });
        });
    }, 1000);
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