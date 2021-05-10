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
          
      </form>
      
  </header>
</template>

<script>


export default {
    name : 'Header',
    props : ['title'],
    components : {
        
    },
    methods : {

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