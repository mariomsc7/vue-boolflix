<template>
  <div id="app">
   <Header title="BOOLFLIX"/>

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
  }
}
</script>

<style lang="scss">
  @import '@/scss/general.scss';
  
</style>
