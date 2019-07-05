<template>
    <b-row>
        <b-col lg="12" v-bind:key="item.type" v-for="item in modules">
            <DocDrop v-if="item.type === 'DocDrop'" v-bind:size="item.size" v-bind:options="item.options"/>
            <DocHeading v-if="item.type === 'DocHeading'" v-bind:text="item.text"/>
            <DocImg v-if="item.type === 'DocImg'" v-bind:src="item.src"/>
            <DocInput v-if="item.type === 'DocInput'" v-bind:size="item.size"/>
            <DocText v-if="item.type === 'DocText'" v-bind:text="item.text" v-bind:size="item.size"/>
        </b-col>
        <b-col lg="12" v-if="modules.length === 0">
            <b-card class="mt-2" id="emptyRow" 
                v-on:dragenter="cancelDefaultEvent"
                v-on:dragover="cancelDefaultEvent"
                v-on:drop="drop(rowId)"
            >
                <p class="m-0 text-center empty">Empty Row</p>
            </b-card>
        </b-col>
     </b-row>
</template>

<script>
import { dragging } from '../App.vue'
import DocDrop from './modules/DocDrop'
import DocInput from './modules/DocInput'
import DocHeading from './modules/DocHeading'
import DocImg from './modules/DocImg'
import DocText from './modules/DocText'

export default {
    name: "Row",
    components: {
        DocDrop,
        DocInput,
        DocHeading,
        DocImg,
        DocText
    },
    props: {
        rowId: Number,
        modules: Array
    },
    methods: {
        cancelDefaultEvent: function (e) {
            e.preventDefault();
        },
        // determines what got dropped onto the empty row and constructs respective componenet
        drop: function(num) {
            if(dragging === 'text' ) {
                this.$parent.$parent.modifyRow(num, {text: 'start typing here', size: 12, type: 'DocText'});
            }
            if(dragging === 'heading') {
                this.$parent.$parent.modifyRow(num, {text: 'Editable Heading', type: 'DocHeading'})
            }
            if(dragging === 'img') {
                this.$parent.$parent.modifyRow(num, {src: 'https://picsum.photos/800', type: 'DocImg'})
            }
            if(dragging === 'input') {
                this.$parent.$parent.modifyRow(num, {size: 12, type: 'DocInput'});
            }
            if(dragging === 'drop') {
                this.$parent.$parent.modifyRow(num, {size: 12, type: 'DocDrop', options:[{value: 'a', text: 'option a'},{value: 'b', text: 'option b'},{value: 'c', text: 'option c'}]});
            }
        }
    }
}
</script>

<style scoped>
#emptyRow {
    background: #dfdfdf;
}
</style>
