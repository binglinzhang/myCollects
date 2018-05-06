<template>
  <ul class="tree-menu">
    <li v-for="(item, index) in data">
      <span @click="toggle(item, index)">
        <i :class="['icon', item.children && item.children.length ? folderIconList[index] : 'file-text']"></i>
        {{ item.menuName }}
      </span>
      <treeMenu :data="item.children" v-if="scope[index]" />
    </li>
  </ul>
</template>

<script>
export default {
  name: 'treeMenu',
  props: {
    data: { type: Array, default: [] }
  },
  data() {
    return {
      folderIconList: [],
      scope: {}
    }
  },
  created() {
    this.data.forEach((item, index) => {
      if (item.children && item.children.length) {
        this.folderIconList[index] = 'folder'
      }
    })
  },
  methods: {
    toggle(item, index) {
      if (item.children && item.children.length) {
        this.$set(this.scope, index, !this.scope[index])
        this.folderIconList[index] = this.scope[index] ? 'folder-open' : 'folder'
      }
    }
  }
}
</script>

<style scoped>
.tree-menu {
  list-style: none;
}
.tree-menu li {
  line-height: 2;
}
.tree-menu li span {
  cursor: default;
}
.icon {
  display: inline-block;
  width: 15px;
  height: 15px;
  background-repeat: no-repeat;
  vertical-align: -2px;
}
.icon.folder {
  background-image: url(/src/assets/folder.png);
}
.icon.folder-open {
  background-image: url(/src/assets/folder-open.png);
}
.icon.file-text {
  background-image: url(/src/assets/file-text.png);
}
.icon.loading {
  background-image: url(/src/assets/loading.gif);
  background-size: 15px;
}
</style>
