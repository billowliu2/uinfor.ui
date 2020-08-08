<template>
  <um-box-row style="height:400px">
    <um-box-col :span="12">
      <um-form-page v-bind="form">
        <el-form-item label="城市：" prop="area">
          <um-select v-model="form.model.area" v-bind="select" />
        </el-form-item>
        <el-form-item label="城市：" prop="area1">
          <um-select v-model="form.model.area1" disabled v-bind="select" />
        </el-form-item>
      </um-form-page>
    </um-box-col>
    <um-box-col :span="12"></um-box-col>
  </um-box-row>
</template>
<script>
export default {
  data() {
    return {
      form: {
        title: '简单下拉列表',
        icon: 'list',
        model: {
          area: '',
          area1: ''
        },
        action: this.submit
      },
      select: {
        method: this.queryOptions
      }
    }
  },
  methods: {
    queryOptions() {
      return new Promise(resolve => {
        resolve([
          {
            label: '南京',
            value: 1
          },
          {
            label: '北京',
            value: 2
          },
          {
            label: '上海',
            value: 3,
            disabled: true
          }
        ])
      })
    },
    submit() {
      return new Promise(resolve => {
        resolve()
      })
    }
  }
}
</script>
