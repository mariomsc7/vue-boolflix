<template>
  <div id="app">

   <Header title="BOOLFLIX" @performSearch="searchFilm" />

   <Main :filter="searchedFilms"/>
  </div>
</template>

<script>
import axios from 'axios'
import Header from '@/components/Header.vue'
import Main from '@/components/Main.vue'

export default {
  name: 'App',
  components: {
    Header,
    Main,
  },
    data() {
      return {
          apiURL : 'https://api.themoviedb.org/3/trending/all/day?api_key=df9d9a316a0d8ce9708918c66df3c99f',
          filmList : [],
          loading : true,
          searchedFilms : []
      }
  },
  created() {
      this.getFilm()
    },
  methods: {
    searchFilm(film) {
      this.searchedFilms = [];
      console.log('log parent', film);
       axios.get('https://api.themoviedb.org/3/search/tv?api_key=df9d9a316a0d8ce9708918c66df3c99f&query=' + film)
            .then(res => {
              console.log(res.data);
              this.filmList = res.data.results;
              this.searchedFilms = this.filmList;
              this.loading = false;
            })
            .catch(err => {
                console.log('Error', err);
            })
      // this.searchedFilms = this.filmList.filter(filter => {
      //   return filter.name.includes(film)
      // }) 
    },
     getFilm() {
            /**
             * API CALL
             */
      axios.get(this.apiURL)
            .then(res => {
              console.log(res.data);
              this.filmList = res.data.results;
              this.searchedFilms = this.filmList;
              this.loading = false;
            })
            .catch(err => {
                console.log('Error', err);
            })
        },
  }
}
</script>

<style lang="scss">
  @import '@/scss/general.scss';
  
</style>
