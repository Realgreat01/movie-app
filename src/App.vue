<template>

<!-- Navigation Bar -->
  <nav>
    <h2 id="app-name">Movie Checking App</h2>
    <button @click="searchToggle = !searchToggle" id="button">
        <span v-if="!searchToggle" id="searchButton">Search Movies</span>
        <span v-else @click="findMovie()" id="getMovie">Get Movies</span>
    </button>
  </nav>

  <!-- Conditional rednering of Search Box -->
  <template v-if="searchToggle">
      <input type="text" id="searchBox" v-model.trim.lazy="searchedKeyword" placeholder="search for movies" @keyup.enter="findMovie()">
  </template>

  <!-- Random Image Box -->
  <SliderComponent :searchResult="searchedKeyword" :searchedMovie="searchedMovie"/>

  <!-- Movie results -->

  <!-- if Movie Result is Available -->
    <div id="movie-container" v-if="searchedMovie">
          <div v-for="(movie, index) in searchedMovie" :key="index" id="movie-box">
            
            <div id="movie-poster">
                <img :src="movie.Poster" :alt="movie.Poster" v-if="movie.Poster != 'N/A'">
                <img v-else src="@/assets/images/no-image.jpg" :alt="movie.Poster">
            </div>

              <!-- Movie Description -->
          <div id="movie-details">
            <div>
                  <h2 id="movie-title">{{movie.Title}}</h2>
                  <h2 id="year-desktop">Production Year : <span id="movie-year">{{movie.Year}}</span></h2>
            </div>
                  <h2><a :href="`https://www.imdb.com/title/${movie.imdbID}`" target="_blank">Watch</a></h2>
          </div>
          <h2 id="year-mobile">Production Year : <span id="movie-year">{{movie.Year}}</span></h2>
            
        </div>
    </div>
 
<!-- if Movie result is not available -->
    <div v-else id="no-result">
      <p id="no-result-emoji">¯\_(ツ)_/¯</p>

        <p id="no-result-message">No result found for 
          <span v-if="searchedKeyword==''">" "</span>
          <span v-else id="no-result-search">" {{searchedKeyword}} "</span>
        </p>
    </div>


</template>

<script>
import SliderComponent from "@/components/SliderComponent";

export default {
  name: 'App',
  data(){
    return{
        searchedKeyword: "EndGamebxbxxbxnxb",
        searchedMovie: [],
        searchToggle: false,
        options: {
            method: 'GET',
            headers: {
              'X-RapidAPI-Key': '03a68834d6msh5d01eef14a1919ep1c6b95jsneddab1d5af6e',
              'X-RapidAPI-Host': 'movie-database-alternative.p.rapidapi.com'
            }
        }
    }
},

  components: {
    SliderComponent,
  },

  methods: {
    // function to fetch Movie Details
        async findMovie(){
            const response = await fetch(`https://movie-database-alternative.p.rapidapi.com/?s=${this.searchedKeyword}&r=json&page=1`, this.options);
            const data = await response.json();
            const {Search} = data;
            return this.searchedMovie=Search
        }
    },

created(){
        this.findMovie()
    }
}
</script>

<style lang="scss">
@import "@/assets/scss/main.scss";
</style>
