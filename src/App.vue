<template>
  <div id="app">
    <TreeBrowser 
      :node="node"
      @onClick="nodeClicked"
    />
  </div>
</template>

<script>
import TreeBrowser from './components/TreeBrowser.vue'
import root from './root.json'

export default {
  name: 'app',
  components: {
    TreeBrowser
  },
  methods: {
    nodeClicked() {
      alert(node.name)
    }
  },
  data() {
    return {
      root,
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
