<template>
  <div id="app">

   <Header title="BOOLFLIX" @performSearch="searchFilm" />

   <Main :filter="searchFilm"/>
  </div>
</template>

<script>
import Header from '@/components/Header.vue'
import Main from '@/components/Main.vue'

export default {
  name: 'App',
  components: {
    Header,
    Main,
  },
  methods: {
    searchFilm(film) {
      console.log('log parent', film);
    },
  }
}
</script>

<style lang="scss">
  @import '@/scss/general.scss';
  
</style>
