<template>
    <main>

        <div v-show="movies.length > 0" class="container">
            <h2>Film</h2>
            <div class="box">
                <Cards
                    v-for="movie in movies"
                    :key="movie.id"
                    :details="movie"
                />
            </div>
        </div>

        <div v-show="series.length > 0" class="container">
            <h2>Serie TV</h2>
            <div class="box">
                <Cards
                    v-for="serie in series"
                    :key="serie.id"
                    :details="serie"
                />
            </div>
        </div>

    </main>
</template>

<script>
import Cards from '@/components/Cards.vue'

export default {
    name: 'Main',
    components: {
        Cards
    },
    props : {
        movies : Array,
        series : Array,
    }
}
</script>

<style scoped lang="scss">
    main {
        padding-top: 100px;
        
    }

    .container {
        padding: 50px;
    }

    .box {
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        align-items: center;
    }

    h2 {
        color: #fff;
        font-size: 2rem;
        margin-bottom: 50px;
    }

</style>