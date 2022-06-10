<template>
  <div id="app">
    <button @click="save">Save</button>
    <v-grid theme="compact" :source="rows" :columns="columns" @aftercolumnsset="debug"></v-grid>
    <div v-if="isSaved">
      <p>What changed?</p>
      <p>{{ JSON.stringify(rows) }}</p>
    </div>
  </div>
</template>

<script>
import VGrid from "@revolist/vue-datagrid";
import { fakeCols, fakeRows } from '../generateFakeData.js';
export default {
  name: "App",
  data() {
    return {
      columns: fakeCols,
      rows: fakeRows,
      isSaved: false
    };
  },
  methods: {
    debug(e) {
      console.log('DEBUG:', e);
    },
    save() {
      this.isSaved = true;
    }
  },
  components: {
    VGrid,
  },
};
</script>

<style>
#app {
  height: 100vh;
  width: 100vh;
}
revo-grid {
  height: 50%;
}
</style>
