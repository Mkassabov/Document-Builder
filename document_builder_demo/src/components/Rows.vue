<template>
    <div>
        <div v-bind:key="row.id" v-for="row in rows">
            <Row v-bind:rowId="row.id" v-bind:modules="row.modules"/>
        </div>
    </div>
</template>

<script>
import Row from './Row.vue'

export default {
    name: "Rows",
    components: {
        Row
    },
    props: ["rows"]
}
</script>

<style scoped>

</style>