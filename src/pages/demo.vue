<template>
  <div>
    <tree-menu :displayMode="false" v-for="(item, index) in treeData" :treeData="item" :key="index" :clickHandle="selectTreeItem"></tree-menu>
  </div>
</template>
<style>

</style>
<script>
import treeMenu from '../components/treeMenu.vue'
export default {
  data () {
    return {
      treeData: [
        {
          id: '1',
          name: '一级菜单A',
          disabled: false,
          child: []
        },
        {
          id: '2',
          name: '一级菜单B',
          child: [
            {
              id: '3',
              name: '二级菜单A',
              child: [
                {
                  id: '4',
                  name: '三级菜单A',
                  child: [],
                  disabled: true
                },
                {
                  id: '5',
                  name: '三级菜单B',
                  child: [],
                  disabled: true
                }
              ],
              disabled: true
            }
          ],
          disabled: true
        },
        {
          id: '6',
          name: '一级菜单C',
          child: [],
          disabled: false
        }
      ]
    }
  },
  methods: {
    selectTreeItem (val) {
      console.log(val)
    }
  },
  components: {
    treeMenu
  }
}
</script>
