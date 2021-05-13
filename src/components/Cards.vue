<template>
    <div class="card-box">
        <!-- POSTER IMAGE -->
        <img v-if="details.poster_path" class="poster" :src="`https://image.tmdb.org/t/p/w300/${details.poster_path}`" alt="">
        <img v-else src="https://www.altavod.com/assets/images/poster-placeholder.png" class="no-poster" alt="">
        <div class="overlay">
            <ul>
                <!-- TITLES -->
                <li class="title">Titolo: <span>{{ details.title ? details.title : details.name }}</span></li>
                <li class="title">Titolo originale: <span>{{ details.original_title ? details.original_title : details.original_name}}</span></li>
                <!-- LANGUAGE -->
                <li>
                    <img v-if="isFlag(details.original_language)"
                        :src="require(`@/assets/images/${details.original_language}.png`)"
                        :alt="details.original_language">
                    <span v-else>Lingua originale: {{ details.original_language }}</span>
                    
                </li>
                <!-- RATING STARS -->
                <li class="rating-stars">Voto:
                    <span>
                        <i class="fas fa-star" v-for="(star, index) in Math.ceil(details.vote_average / 2)" :key="index"></i>
                        <i class="far fa-star" v-for="(star, index) in 5 - Math.ceil(details.vote_average / 2)" :key="index"></i>
                    </span>
                </li>
                <li>Trama: 
                    <div class="overview">
                        {{ details.overview }}
                    </div> 
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
    
    .card-box {
        position: relative;
        cursor: pointer;
        width: 350px;
        height: 500px;     
        transition: opacity .3s;
        &:hover {
            .overlay {
                opacity: 1
            }
        }
    }

    .card-box .poster,
    .card-box .no-poster {
        width: 100%;
        height: 100%;
    }


    .overlay {
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100%;
        width: 100%;
        position: absolute;
        top: 0;
        left: 0;
        color: white;
        text-align: center;
        padding: 10px;
        transition: opacity .3s;
        opacity: 0;
        background: rgba(0, 0, 0, .5)
    }

    .overlay .title {
        margin-bottom: 10px;
    }

    .overlay .title span {
        font-weight: bold;
    }

    .overlay .rating-stars {
        margin: 10px 0;
        
    }

    .overlay .rating-stars i {
        color: gold;
    }

    .overlay .overview {
        height: 200px;
        padding: 10px;
        overflow-y: auto;
        text-align: left;
    }

    ul {

        max-height: 350px;
        list-style: none;
        
        
    }
    li img {
        width: 24px;
    }
</style>