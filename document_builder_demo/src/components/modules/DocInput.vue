<template>
    <div>
        <div class="mt-2"></div>
        <b-form-input v-bind:placeholder="'input field'"></b-form-input>
    </div>
</template>

<script>

export default {
    name: "DocInput",
    props: {
        size: Number
    },
    data() {
        return {
          minSize: 6,
          type: 'DocInput'
        }
    } 
}
</script>

<style scoped>

</style>
