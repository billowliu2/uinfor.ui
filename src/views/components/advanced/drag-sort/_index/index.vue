<template>
  <um-tmpl v-bind="tmpl"></um-tmpl>
</template>
<script>
import page from './page.js'
import attrs from './data/attrs.js'
import events from './data/events'
export default {
  name: page.name,
  data() {
    return {
      tmpl: {
        title: '拖动排序(um-drag-sort)',
        icon: 'list',
        attrs,
        events
      }
    }
  },
  created() {
    this.setTabName(this.tmpl.title)
  }
}
</script>
