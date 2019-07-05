<template>
    <div>
        <div class="mt-2"></div>
        <b-form-select v-model="selected">
            <option :value="null">Please select an option</option>
            <option :value="option.value" v-bind:key="option.value" v-for="option in options">
                {{option.text}}
            </option>
        </b-form-select>
    </div>
</template>

<script>
export default {
    name: "DocDrop",
    props: {
        size: Number,
        options: Array
    },
    data() {
        return {
            selected: null,
            minSize: 6,
            type: 'DocDrop'
        }
    } 
}
</script>

<style scoped>

</style>
