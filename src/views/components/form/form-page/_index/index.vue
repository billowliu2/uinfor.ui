<template>
  <um-tmpl v-bind="tmpl">
    <el-alert title="说明" type="warning" show-icon :closable="false">
      <p>页表单组件会填充满整个父级元素，所以一般当成一个页面级组件使用</p>
    </el-alert>
  </um-tmpl>
</template>
<script>
import page from './page.js'
import attrs from './data/attrs.js'
import methods from './data/methods'
import events from './data/events.js'
export default {
  name: page.name,
  data() {
    return {
      tmpl: {
        title: '页表单(um-form-page)',
        icon: 'list',
        attrs,
        methods,
        events
      }
    }
  },
  created() {
    this.setTabName(this.tmpl.title)
  }
}
</script>
