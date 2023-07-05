<script>
export default {
    props: {
        listItem: Array
    }
}
</script>

<template>
    <ul>
        <li v-for="item in listItem" key="item">
            <span>Titolo originale: {{ item.originalTitle }}</span> <br>
            <span>Titolo in Italiano: {{ item.itTitle }}</span> <br>
            <span v-if="item.originalLanguage === 'en' || item.originalLanguage === 'it'"><img
                    :src="`./src/assets/img/${item.originalLanguage}.png`" :alt="`flag ${item.originalLanguage}`"></span>
            <span v-else>Lingua: {{ item.originalLanguage }}</span> <br>
            <span>Voto: {{ item.vote }}</span> <br>
        </li>
    </ul>
</template>


<style scoped>
img {
    max-width: 40px;
    height: auto;
}
</style>