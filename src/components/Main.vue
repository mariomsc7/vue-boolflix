<template>
<main class="movies">
    <div v-if="!loading">
        <div v-for="film in filmList" :key="film.id" class="filmBox">

        <Film :info='film'/>

        </div>
    </div>
    <div v-else class="loader">Loading...</div>
</main>

</template>

<script>
import axios from 'axios';
import Film from '@/components/Film.vue'


export default {
    name: 'Main',
    components: {
        Film
    },
    data() {
        return {
            apiURL : 'https://api.themoviedb.org/3/search/tv?api_key=df9d9a316a0d8ce9708918c66df3c99f&query=avengers',
            filmList : [],
            loading : true
        }
    },
    created() {
        this.getFilm()
    },
    methods : {
        getFilm() {
            /**
             * API CALL
             */
            axios.get(this.apiURL)
            .then(res => {
                console.log(res.data);
                this.filmList = res.data.results;
                this.loading = false;
            })
            .catch(err => {
                console.log('Error', err);
            })
        },
    
    }
}
</script>

<style scoped lang="scss">
    .filmBox {
        margin-bottom: 30px;
    }
</style>