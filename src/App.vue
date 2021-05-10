<template>
  <div id="app">
    
   <Header title="BOOLFLIX" @performSearch="searchFilm" />

   <Main />
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
    searchFilm() {
      console.log('log parent');
    },
  }
}
</script>

<style lang="scss">
  @import '@/scss/general.scss';
  
</style>
