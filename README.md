# vue-tree-component

> A Vue.js project

## Build Setup

``` bash
# 安装相关依赖
npm install

# 启动项目
npm run dev

# 参数说明

  // displayMode
  true => 不显示 disabled 为 true 的节点及子节点
  false => disabled 为 true 的节点及子节点置灰

  // treeData
  树形结构数据, 其中
  disabled => Boolean
  child => Array

  // selectTreeItem
  Function(param)
  param => 当前节点TreeData的所有数据


