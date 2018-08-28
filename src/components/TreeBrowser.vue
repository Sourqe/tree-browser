<template>
  <div>
    <div 
      class="node-names"
      :style="{'margin-left': `${depth * 20}px`}"
      @click="expand = !expand"
    >
      {{node.name}}
    </div>
    
    <TreeBrowser
      v-if="expand"
      v-for="child in node.children"
      :key="child.name"
      :node="child"
      :depth="depth + 1" 
    />
  </div>
</template>

<script>
export default {
  data() {
    return {
      expand: false,
    }
  },
  props: {
    depth: {
      type: Number,
      default: 0
    },
    node: Object,
  },
  name: 'TreeBrowser',
}
</script>

<style scoped>
.node-names {
  font-size: 20px;
  text-align: left;
}
</style>
