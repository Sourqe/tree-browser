<template>
  <div>
    <div 
      class="node-names"
      :style="{'margin-left': `${depth * 20}px`}"
      @click="expand = !expand"
    >
      <span 
        v-if="hasChildren"
        class="type"
      >
        {{expand ? '&#9660;' : '&#9658;'}}
      </span>

      <span v-else>&#9671;</span>
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
  computed: {
    hasChildren() {
      return this.node.children
    }
  }
}
</script>

<style scoped>
.node-names {
  font-size: 20px;
  text-align: left;
}
</style>
