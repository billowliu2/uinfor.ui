<template>
  <um-tmpl v-bind="tmpl">
    <el-alert type="warning" show-icon :closable="false">该组件主要时为了控制Element-UI里面的标签页组件布局用的，他能够让内部的el-tabs标签高度100%</el-alert>
  </um-tmpl>
</template>
<script>
import page from './page.js'
import attrs from './data/attrs.js'
import slots from './data/slots.js'
import methods from './data/methods.js'
import events from './data/events.js'
export default {
  name: page.name,
  data() {
    return {
      val: '',
      tmpl: {
        title: '标签页(um-tabs)',
        icon: 'card',
        attrs,
        slots,
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
