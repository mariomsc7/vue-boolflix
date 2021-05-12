<template>
  <header>
      
      <!-- LOGO -->
      <a href="">BOOLFLIX</a>
      <!-- INPUT SEARCH -->
      <form>
          <input 
          type="text"
          placeholder="Cerca"
          class="search-input"
          v-model.trim="searchInput"
          >
          <button
           type="submit"
            @click.prevent="$emit('performSearch', searchInput)">search</button>
      </form>
      
  </header>
</template>

<script>


export default {
    name : 'Header',
    props : ['title'],
    components : {
        
    },
    data() {
        return {
            searchInput: '',
        }
    },
}
</script>

<style scoped lang="scss">
    header {
        display: flex;
        justify-content: space-between;
        padding: 50px;
    }
    
</style>