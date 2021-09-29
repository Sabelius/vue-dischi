<template>
<div class=" container-fluid">
    <div class="row">
        <div class="col-15  header-container d-flex">
          <img src="https://www.michelafranceschina.it/Burattini_Erranti/files/stacks-image-c5a4a2c.jpg">
        </div>
    </div>
</div>
  
</template>

<script>
export default {
    name: "Header",

}
</script>

<style lang="scss" scoped>
@import "../style/variables.scss";

.header-container{
   background-color:  $back-ground;
}
img{
    width: 80px;
    cursor: pointer;
    border-radius: 100%;
}

</style>