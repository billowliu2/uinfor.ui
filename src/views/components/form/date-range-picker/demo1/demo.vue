<template>
  <um-list ref="list" v-bind="list">
    <!--日期过滤-->
    <template v-slot:header-toolbar>
      <um-date-range-picker size="mini" :start.sync="list.model.startDate" :end.sync="list.model.endDate" @change="refresh" />
    </template>
  </um-list>
</template>
<script>
export default {
  data() {
    return {
      curr: { id: '' },
      list: {
        title: '时间段组件示例代码',
        cols: [],
        action: () => {
          return new Promise(resolve => {
            resolve({ code: 0, data: { row: [] } })
          })
        },
        model: {
          startDate: null,
          endDate: null
        }
      }
    }
  },
  methods: {
    refresh() {
      this.$refs.list.refresh()
    }
  }
}
</script>
