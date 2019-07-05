<template>
    <div>
        <div class="mt-2"></div>
        <p contenteditable="true" @blur="onEdit" v-text="this.text"></p>
    </div>
</template>

<script>

export default {
    name: "DocText",
    props: {
        text: String,
        size: Number
    },
    methods: {
        // modifies the row in App.vue to ensure all data is in one place
        onEdit: function(e) {
            let src = this.text = e.target.textContent;
            this.$parent.$parent.$parent.modifyRow(this.$parent.rowId, {text: src, size: this.size, type: 'DocText'})
        }
    },
    data() {
        return {
            minSize: 6,
            type: 'DocText'
        }
    }
}
</script>

<style scoped>

</style>
