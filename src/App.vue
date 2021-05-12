<template>
  <div id="app">

   <Header @performSearch="getData" />

   <Main :movies="movieList" :series="tvList"/>

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
          apiURL : 'https://api.themoviedb.org/3/search/',
          apiKey : 'df9d9a316a0d8ce9708918c66df3c99f',
          movieList : [],
          tvList : [],
      }
  },
  methods: {
    getData(searchInput) {
      console.log(searchInput);

      if( searchInput !== '') {

        const apiParams = {
                api_key : this.apiKey,
                query : searchInput,
                language : 'it-IT'
              };

          /**
           * MOVIES CALL
           */
          axios.get(this.apiURL + 'movie', {
              params : apiParams,
          }).then(res => {
            this.movieList = res.data.results;
          });
          /**
           * TV SERIES CALL
           */
          axios.get(this.apiURL + 'tv', {
              params : apiParams,
          }).then(res => {
            this.tvList = res.data.results;
          });
      }
    },
  }
}
</script>

<style lang="scss">
  
  
</style>
