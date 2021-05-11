<template>
<main class="movies">
    <div v-if="filter.length > 0">
        
        <div v-for="film in filter" :key="film.id" class="filmBox">

        <Film :info='film'/>

        </div>
    </div>
    <div v-else class="loader">Loading...</div>
</main>

</template>

<script>

import Film from '@/components/Film.vue'

export default {
    name: 'Main',
    props: ['filter'],
    components: {
        Film
    },


    methods : {

    
    }
}
</script>

<style scoped lang="scss">
    .filmBox {
        margin-bottom: 30px;
    }
</style>