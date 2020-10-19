<template>
  <div>
      <div class="treenode" @click="toggle">
        <label>{{model.title}}</label>
        <span v-if="isFolder">[{{open?"-":"+"}}]</span>
      </div>
      <div v-show="open" v-if="isFolder">
        <tree-node v-for="item in model.children" :key="item.title" :model="item"></tree-node>
      </div>
  </div>
</template>

<script>
export default {
  name:'tree-node',
  props: {
    model: {
      type: Object,
    },
  },
  data() {
    return {
      open:false
    }
  },
  methods: {
    toggle() {
      if(this.isFolder){
        this.open=!this.open;
      }
    }
  },
  computed: {
    isFolder() {
      return this.model.children&&this.model.children.length>0
    }
  },
}
</script>

<style>

</style>