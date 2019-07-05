<template>
    <div>
        <h1 contenteditable="true" @blur="onEdit" v-text="this.text"></h1>
    </div>
</template>

<script>

export default {
    name: "DocHeading",
    props: {
        text: String,
    },
    methods: {
        // modifies the row in App.vue to ensure all data is in one place
        onEdit: function(e) {
            let src = this.text = e.target.textContent;
            this.$parent.$parent.$parent.modifyRow(this.$parent.rowId, {text: src, type: 'DocHeading'})
        }
    },
    data() {
        return {
            size: 12,
            type: 'DocHeading'
        }
    }
}
</script>

<style scoped>

</style>
