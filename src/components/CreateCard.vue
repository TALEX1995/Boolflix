<script>
export default {
    props: {
        listItem: Array
    }
}
</script>

<template>
    <ul>
        <li v-for="item in listItem">
            <span>Titolo originale: {{ item.originalTitle }}</span> <br>
            <span>Titolo in Italiano: {{ item.itTitle }}</span> <br>
            <span>Lingua: {{ item.originalLanguage }}</span> <br>
            <span>Voto: {{ item.vote }}</span> <br>
        </li>
    </ul>
</template>


<style></style>