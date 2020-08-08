<template>
  <um-box page header title="拖拽排序示例" icon="sort">
    <um-box-row height="400px">
      <um-box-col :span="12">
        <um-drag-sort style="width:500px" v-model="list" />
      </um-box-col>
      <um-box-col :span="12">
        <textarea rows="50" cols="100" :value="listJson"></textarea>
      </um-box-col>
    </um-box-row>
  </um-box>
</template>
<script>
export default {
  data() {
    let list = []
    for (var i = 1; i < 10; i++) {
      list.push({
        id: i,
        label: `第${i}个`,
        sort: i
      })
    }
    return {
      list
    }
  },
  computed: {
    listJson() {
      return JSON.stringify(this.list, null, 2)
    }
  }
}
</script>
