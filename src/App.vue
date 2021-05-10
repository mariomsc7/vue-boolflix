<template>
  <div id="app">

   <Header title="BOOLFLIX" @performSearch="searchFilm" />

   <Main :filter="searchFilm"/>
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
  created() {
      this.getFilm()
    },
  methods: {
    searchFilm(film) {
      console.log('log parent', film);
    },
     getFilm() {
            /**
             * API CALL
             */
      axios.get(this.apiURL)
            .then(res => {
              console.log(res.data);
              this.filmList = res.data.results;
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
