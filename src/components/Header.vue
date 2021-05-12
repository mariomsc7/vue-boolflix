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
          <button class="btn" @click.prevent="$emit('performSearch', searchInput)">
              <i class="fas fa-search"></i>
          </button>
          

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
        padding: 20px;
        background: #141414;
    }

    .logo {
        width: 200px;
    }

    .logo img {
        width: 100%;
    }

    .search-input {
        outline: none;
        padding: 10px;
        background: transparent;
        color: #fff;
        margin-right: 10px;
        border: 1px solid;
    }

    .btn {
        cursor: pointer;
        margin-right: 100px;
        padding: 10px;
        outline: none;
        background: transparent;
        border: 1px solid #fff;
        &:hover {
            background: #888;
        }
    }
    .btn i {
        color: #fff;
    }


</style>