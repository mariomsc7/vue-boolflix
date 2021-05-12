<template>
    <div class="card-box">
        <!-- POSTER IMAGE -->
        <img class="poster" :src="`https://image.tmdb.org/t/p/w300/${details.poster_path}`" alt="">
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
                     {{ details.overview}}
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
        width: 350px;
        height: 500px;
        padding: 15px;
        transition: opacity .3s;
        &:hover {
            opacity: .4;
        }
    }

    .card-box .poster {
        width: 100%;
        height: 100%;
    }


    .overlay {
        position: relative;
        color: white;
        
        text-align: center;
        
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
        display: flex;
        flex-direction: column;
        position: absolute;
        bottom: 20px;
        list-style: none;
        padding: 10px;
        
    }
    li img {
        width: 24px;
    }
</style>