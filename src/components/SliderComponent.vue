<template>
  <img :src="image" alt="">
  <h2 v-if="searchedMovie">
    Search results for " <span id="result">{{searchResult}} </span> "
  </h2>
</template>

<script>
export default {
    name: "SliderComponent",
    data(){
        return {
            imageSource:"Heal.jpeg"
        }
    },
    props:{
        searchResult: String,
        searchedMovie: Array
    },
    computed : {
        image(){
            return `https://picsum.photos/800/200`;
        }
    }
}
</script>

<style lang="scss" scoped>

@import "@/assets/scss/main.scss";

h2{ 
        color: $primary;
        margin: 30px 0;
        margin-left: 100px;
        font-weight: 400;
        #result{
        color: $year;
        border-bottom: 1px solid $text;
        padding: 0 10px;
    }
}
 img{
    width: 100%;
    display:block;
    object-fit: center;
    height: 200px;
    border-radius: 10px;
 }

 @media only screen and (max-width: 600px) {
    h2{
        margin-left: 10px;
        font-size: 12px;
    }
 img{
    width: 90%;
    display:block;
    object-fit: center;
    margin:0 auto;
    border-radius: 5px;
 }
 }
</style>