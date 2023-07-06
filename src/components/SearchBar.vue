<script>
export default {
    data() {
        return {
            searchedTerm: '',
        }
    },
    props: {
        labelInput: String,
        placeholder: String,
    },

    emits: ['form-submit']
}
</script>

<template>
    <form @submit.prevent="$emit('form-submit', searchedTerm), searchedTerm = ''">
        <div class="form-group">
            <input :placeholder="placeholder" v-model.trim="searchedTerm" type="text" class="form-control mx-3 w-50">
            <button class="btn btn-primary">Cerca</button>
        </div>
    </form>
</template>

<style lang="scss" scoped>
form {
    width: 50%;

    .form-group {
        display: flex;
        align-items: center;
        justify-content: flex-end;
    }
}
</style>