<template>
  <div>
    <div 
      class="node-names"
      :style="{'margin-left': `${depth * 20}px`}"
      @click="nodeClick()"
    >
      <span 
        v-if="hasChildren"
        class="type"
      >
        {{expand ? '&#9660;' : '&#9658;'}}
      </span>

      <span class="type" v-else>&#9671;</span>

      <span 
        :style="getStyle(node)"
      >
        {{node.name}}
      </span>
    </div>
    
    <TreeBrowser
      v-if="expand"
      v-for="child in node.children"
      :key="child.name"
      :node="child"
      @onClick="(node) => $emit('onClick', node)"
      :depth="depth + 1" 
    />
  </div>
</template>

<script>
import * as ColorHash from 'color-hash'

const colorHash = new ColorHash()

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
  },
  methods: {
    nodeClick() {
      this.expand = !this.expand

      if (!this.hasChildren) {
        this.$emit('onClick', this.node)
      }
    },
    getStyle(node) {
      if (node.children) {
        return {
          'color': 'white',
        }
      } else {
        return {
          'color': colorHash.hex(node.name.split('.')[1])
        }
      }
    }
  }
}
</script>

<style scoped>
.node-names {
  font-size: 20px;
  text-align: left;
}

.type {
  margin-left: 10px;
}
</style>
