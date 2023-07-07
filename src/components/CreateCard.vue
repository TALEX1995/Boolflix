<script>
export default {
    props: {
        item: Object,
    },

    computed: {
        hasFlag() {
            return this.item.originalLanguage === 'en' || this.item.originalLanguage === 'it'
        },

        getFlagSrc() {
            const url = new URL(`../assets/img/${this.item.originalLanguage}.png`, import.meta.url);

            return url.href
        },

        srcPoster() {
            // return this.item.posterUrl ? this.item.posterUrl : 'aaa'
            let posterUrl = ''
            if (this.item.posterUrl.includes('null')) {
                posterUrl = 'https://prestashop.com/sites/default/files/wysiwyg/404_not_found.png'
            } else {
                posterUrl = this.item.posterUrl
            }
            return posterUrl
        }
    },

    methods: {
        starIcon(n) {
            return this.item.vote >= n ? 'fas' : 'far'
        }
    }
}
</script>

<template>
    <ul class="poster-container mt-5">
        <li>
            <img class="poster" :src="srcPoster" :alt="item.originalTitle">
        </li>

        <li class="text-product">
            <div><span class="bold-text">Titolo originale:</span> {{ item.originalTitle }}</div>
            <div><span class="bold-text">Titolo in Italiano:</span> {{ item.itTitle }}</div>

            <!-- Condition to change language in a flag if they are en or it -->
            <div v-if="this.hasFlag">
                <img class="flag" :src="getFlagSrc" :alt="item.originalLanguage">
            </div>
            <div v-else><span class="bold-text">Lingua:</span> {{ item.originalLanguage }}</div>
            <div>
                <span class="bold-text">Voto</span>
                <!-- Cicle to change vote in star -->
                <span v-for="index in 5" :key="index"><font-awesome-icon :icon="[starIcon(index), 'star']" />
                </span>

            </div>
            <div><span class="bold-text">Overview:</span> {{ item.overview }}</div>
        </li>
    </ul>
</template>


<style lang="scss" scoped>
@use '../assets/scss/vars' as *;

img.flag {
    max-width: 40px;
    height: auto;
}

img.poster {
    width: 100%;
    min-height: 513px;
}

span.bold-text {
    font-weight: 700;
}

.poster-container {

    &:hover .poster {
        display: none;
    }

    &:hover .text-product {
        display: block;
    }

    .text-product {
        overflow: auto;
        display: none;
        background-color: $body-bkg;
        color: white;
        padding: $rem05 $rem05;
        max-height: 513px;
    }
}
</style>
