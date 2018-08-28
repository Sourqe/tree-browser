<template>
  <div id="app">
    <h1>Tree Browser in Vue</h1>
    <TreeBrowser 
      :node="node"
      @onClick="nodeClicked"
    />
  </div>
</template>

<script>
import TreeBrowser from './components/TreeBrowser.vue'
import node from './root.json'

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
      node,
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
  margin-top: 60px;
}

body {
  background-color: black;
  color: white;
}
</style>
