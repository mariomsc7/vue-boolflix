<template>
    <div class="film-box">
        <div>

        </div> 
        <ul>
            <li>Name: {{ info.name }}</li>
            <li>Original name: {{ info.original_name }}</li>
            <li>Language: {{ info.original_language }}</li>
            <li>Vote:  {{ info.vote_average }}</li>
        </ul>
    </div>
</template>

<script>
export default {
    name : 'Film',
    props: ['info']
}
</script>

<style scoped lang="scss">
    ul {
        padding: 10px;
    }
</style>