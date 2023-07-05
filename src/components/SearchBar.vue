<script>
export default {
    data() {
        return {
            searchedTerm: '',
        }
    },
    props: {
        labelInput: String,
    },

    emits: ['form-submit']
}
</script>

<template>
    <form class="w-50" @submit.prevent>
        <div class="form-group">
            <label for="input-text">{{ labelInput }}</label>
            <input v-model.trim="searchedTerm" type="text" class="form-control" id="input-text">
            <button @click="$emit('form-submit', searchedTerm), searchedTerm = ''">Cerca</button>
        </div>
    </form>
</template>

<style></style>