<template>
  <div class="container">
     <div class="row">
       <div v-for="cd in musics" :key="cd" class="col-lg-3 col-md-4 col-sm-6 col-12 pt-5">
         <div class="cd-container m-1">
            <img :src="cd.poster" class="pt-3">
       <h4 class="pt-3">{{ cd.title }}</h4>
       <h5>{{ cd.author }}</h5>
       <h6>{{ cd.year }}</h6>
         </div>
       </div>
     </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: "Discs",

  data() {
    return{
      musics : []
    }
  },
  created() {
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
    .then((response) =>{
     this.musics = response.data.response.slice();
    })
  }
};
</script>

<style lang="scss" scoped>
@import "../style/variables.scss";

.cd-container{
  background-color: rgb(45, 53, 83);
  width: 70%;
  cursor: pointer;
}
img{
  width: 60%;
}

h4{
  color:$title-color;
}

h5, 
h6{
 color: $subtitle-color;
}
</style>
