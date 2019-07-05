<template>
  <div id="app">

    <b-container>

      <b-row class="mt-5">
        <b-col lg="8">
          <b-card class="m-3">
            <Rows v-bind:rows="rows" />
          </b-card>
        </b-col>
        <b-col lg="4">
          <b-card class="m-3">
            <b-row class="d-flex justify-content-center">
              <b-button class="m-2" variant="primary" @click="addRow">Add Row</b-button>
              <b-button class="m-2" variant="success" @click="save">Save</b-button>
              <b-button class="m-2" variant="danger" @click="deleteDoc">Delete</b-button>
            </b-row>
            <b-row class="d-flex justify-content-center">
              <b-card class="w-75 mb-2" v-on:dragstart="dragStart('heading')" draggable="true"> 
                <p class="m-0 text-center" draggable="false"> Add Heading </p>
              </b-card>
              <b-card class="w-75 mb-2" v-on:dragstart="dragStart('text')" draggable="true"> 
                <p class="m-0 text-center" draggable="false"> Add Text </p>
              </b-card>
              <b-card class="w-75 mb-2" v-on:dragstart="dragStart('img')" draggable="true"> 
                <p class="m-0 text-center" draggable="false"> Add Image </p>
              </b-card>
              <b-card class="w-75 mb-2" v-on:dragstart="dragStart('drop')" draggable="true"> 
                <p class="m-0 text-center" draggable="false"> Add Dropdown Menu </p>
              </b-card>
              <b-card class="w-75 mb-2" v-on:dragstart="dragStart('input')" draggable="true"> 
                <p class="m-0 text-center" draggable="false"> Add Input </p>
              </b-card>
            </b-row>
          </b-card>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>

var dragging;
export { dragging }

import Rows from './components/Rows.vue'

export default {
  name: 'app',
  components: {
    Rows
  },
  methods: {
    // adds another row to data
    addRow() {
      this.rows = [...this.rows, {id: this.rows.length, modules: []}]
    },
    // saves data (theoretically this would post to a server)
    save() {
      console.log(this.rows);
    },
    // clears all data
    deleteDoc() {
      this.rows = [
        {
          id: 0,
          modules: []
        }
      ]
    },
    // sets dragging to the item currently being dragged
    dragStart(dragType) {
      dragging = dragType;
    },
    // allows modification of rows from other components
    modifyRow(num, newModule) {
      this.rows[num].modules = [newModule]
    }
  },
  data() {
    // Doc data is held here
    return {
      rows: [
        {
          id: 0,
          modules: []
        }
      ]
    }
  }
}

</script>

<style>
  @import url('https://fonts.googleapis.com/css?family=Roboto:400,700');

  body {
    background: #EEF1F4;
    font-family: 'Roboto', sans-serif;
  }
</style>
