<template>
    <div>
        <b-img v-bind:src="this.src" fluid alt="Responsive image"></b-img>
    </div>
</template>

<script>

export default {
    name: "DocImg",
    props: {
        src: String,
    },
    data() {
        return {
            size: 12,
            type: 'DocImg'
        }
    }
}
</script>

<style scoped>

</style>
