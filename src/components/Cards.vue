<template>
    <div class="card-box">
        <!-- POSTER IMAGE -->
        <img :src="`https://image.tmdb.org/t/p/w300/${details.poster_path}`" alt="">
        <div class="overlay">
            <ul>
            <!-- TITLES -->
            <li>Titolo: {{ details.title ? details.title : details.name }}</li>
            <li>Titolo originale: {{ details.original_title ? details.original_title : details.original_name}}</li>
            <!-- LANGUAGE -->
            <li>
                <img v-if="isFlag(details.original_language)"
                    :src="require(`@/assets/images/${details.original_language}.png`)"
                    :alt="details.original_language">
                <span v-else>Lingua originale: {{ details.original_language }}</span>
                
            </li>
            <!-- RATING STARS -->
            <li>Voto:
                <span>
                    <i class="fas fa-star" v-for="(star, index) in Math.ceil(details.vote_average / 2)" :key="index"></i>
                    <i class="far fa-star" v-for="(star, index) in 5 - Math.ceil(details.vote_average / 2)" :key="index"></i>
                </span>
            </li>
            </ul>
        </div>

    </div>
</template>

<script>
export default {
    name : 'Cards',
    props : {
        details : Object,
    },
    data() {
        return {
            flagsIMG: ['it', 'en']
        }
    },
    methods : {
        isFlag(lang) {
            return this.flagsIMG.includes(lang)
        }
    }
}
</script>

<style scoped lang="scss">

    .overlay {
        position: relative;
    }

    ul {
        position: absolute;
    }
    li img {
        width: 24px;
    }
</style>