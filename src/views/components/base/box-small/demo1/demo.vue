<template>
  <um-box page>
    <um-box-row>
      <um-box-col :span="6">
        <um-box-small v-bind="box" @more="onMore" />
      </um-box-col>
      <um-box-col :span="6">
        <um-box-small v-bind="box1" @more="onMore" />
      </um-box-col>
      <um-box-col :span="6">
        <um-box-small v-bind="box2" />
      </um-box-col>
    </um-box-row>
  </um-box>
</template>
<script>
export default {
  data() {
    return {
      box: {
        label: '总消费额',
        value: 12352.11,
        unit: '元',
        icon: 'money',
        more: true
      },
      box1: {
        label: '总收入',
        value: 42352.11,
        unit: '元',
        icon: 'money',
        more: true,
        bgColor: 'warning'
      },
      box2: {
        label: '总支出',
        value: 562352.11,
        unit: '元',
        icon: 'money',
        bgColor: 'primary'
      }
    }
  },
  methods: {
    onMore() {
      this._success('没有更多了~')
    }
  }
}
</script>
