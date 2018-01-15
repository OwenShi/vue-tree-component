<template>
  <div class="treeMenu">
    <div class="treeItem" v-if="!displayMode" :class="{ disabled: treeData.disabled }">
      <div @click="toggle" v-if="open" class="select1"></div>
      <div @click="toggle" v-if="!open" class="select"></div>
      <span @click="clickHandle(treeData)">{{treeData.name}}</span>
      <tree-menu v-for="(item, index) in treeData.child"
                 v-show="open"
                 v-if="isFolder"
                 :key="index"
                 :treeData="item"
                 :clickHandle="clickHandle"></tree-menu>
    </div>
    <div class="treeItem" v-if="displayMode&&treeData.disabled">
      <div @click="toggle" v-if="open" class="select1"></div>
      <div @click="toggle" v-if="!open" class="select"></div>
      <span @click="clickHandle(treeData)">{{treeData.name}}</span>
      <tree-menu v-for="(item, index) in treeData.child"
                 v-show="open"
                 v-if="isFolder"
                 :key="index"
                 :treeData="item"
                 :clickHandle="clickHandle"></tree-menu>
    </div>
  </div>
</template>
<style scoped>
  .treeMenu {
    /*height:100%;*/

  }

  .treeMenu .treeItem {
    list-style: none;
    font-size: 0.7rem;
    margin-top: 0.2rem;
    margin-left: 1rem;
    text-align: left;
  }

  .disabled {
    color: #C0C0C0
  }

  .select {
    background: url("../../static/images/up2.png") no-repeat top left;
    background-size: 0.9rem 0.9rem;
    width: 0.9rem;
    height: 0.9rem;
    display: inline-block;
  }
  .select1 {
    background: url("../../static/images/down2.png") no-repeat top left;
    background-size: 0.9rem 0.9rem;
    width: 0.9rem;
    height: 0.9rem;
    display: inline-block;
  }

  .treeItem span {
    cursor: pointer;
  }
</style>
<script>
  /**
   * treeMenu 1.0.0
   * Copyright 2018-01-03 @shiwj
   * rely: none
   */
  export default {
    name: 'treeMenu',
    data () {
      return {
        open: false
      }
    },
    props: {
      displayMode: {
        type: Boolean,
        default: true
      },
      treeData: {
        type: Object
      },
      clickHandle: {
        type: Function,
        default: function () {
          console.log('----')
        }
      }
    },
    computed: {
      isFolder () {
        return this.treeData.child && this.treeData.child.length
      }
    },
    methods: {
      toggle (index) {
        if (this.isFolder) {
          this.open = !this.open
        }
      },
      selectItem (data) {
        console.log(data)
      }
    }
  }
</script>

