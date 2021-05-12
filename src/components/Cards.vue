<template>
    <div class="film-box">
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
                    
                </span>
            </li>
        </ul>
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
    li img {
        width: 24px;
    }
</style>