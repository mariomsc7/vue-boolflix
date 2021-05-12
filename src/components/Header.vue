<template>
  <header>

      <!-- LOGO -->
      <div class="logo">
          <img src="https://fontmeme.com/permalink/210512/b84f67a16fb1d9d9325b6b95003a4be8.png" alt="">
      </div>
          
      
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
        align-items: center;
        padding: 50px;
        background: #141414;
    }


    
</style>