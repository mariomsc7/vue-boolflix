<template>
    <main>

        <div v-show="movies.length > 0" class="movies">
            <h2>Film</h2>
            <div>
                <Cards
                    v-for="movie in movies"
                    :key="movie.id"
                    :details="movie"
                />
            </div>
        </div>

        <div v-show="series.length > 0" class="series">
            <h2>Serie TV</h2>
            <div>
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
    .filmBox {
        margin-bottom: 30px;
    }
</style>