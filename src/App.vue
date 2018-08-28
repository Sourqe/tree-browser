<template>
  <div id="app">
    <TreeBrowser 
      :node="node"
    />
  </div>
</template>

<script>
import TreeBrowser from './components/TreeBrowser.vue'

export default {
  name: 'app',
  components: {
    TreeBrowser
  },
  data() {
    return {
      node: {
        name: '/',
        children: [
          {
            name: 'music',
            children: [
              {
                name: 'mp3'
              }
            ]
          },
          {
            name: 'workspace', 
            children: [
              {
                name: 'source.js'
              }
            ]
          }
        ]
      }
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
