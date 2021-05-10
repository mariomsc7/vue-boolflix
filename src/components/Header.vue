<template>
  <header>
      <h1>{{title}}</h1>
      <form>
          <input 
          type="text"
          placeholder="Cerca"
          class="search-input"
          v-model="searchFilm"
          >
          <Search @performSearch="searchFilm" />
      </form>
      
  </header>
</template>

<script>
import Search from '@/components/Search.vue'

export default {
    name : 'Header',
    props : ['title'],
    components : {
        Search
    },
    methods : {
        searchFilm() {
            console.log('log parent');
        },
        
    }
}
</script>

<style scoped lang="scss">
    header {
        display: flex;
        padding: 20px;
        align-items: center;
    }
    
</style>