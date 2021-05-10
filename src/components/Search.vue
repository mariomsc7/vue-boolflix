<template>
  <div>
      <button type="submit" @click.prevent="$emit('performSearch', searchFilm)">search</button>
  </div>
</template>

<script>
export default {
    name : 'Search',
    data() {
        return {
            searchFilm: '',
        }
    },
}

</script>

<style>

</style>