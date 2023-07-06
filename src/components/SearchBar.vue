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
    <form class="w-50" @submit.prevent="$emit('form-submit', searchedTerm), searchedTerm = ''">
        <div class="form-group">
            <label for="input-text">{{ labelInput || 'cerca' }}</label>
            <input v-model.trim="searchedTerm" type="text" class="form-control" id="input-text">
            <button>Cerca</button>
        </div>
    </form>
</template>

<style></style>