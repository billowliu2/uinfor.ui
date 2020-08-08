<template>
  <um-container>
    <um-split v-model="split">
      <template v-slot:left>
        <um-box page header title="标签页示例" icon="list">
          <el-tree :data="data" show-checkbox node-key="id" :default-expanded-keys="[2, 3]" :default-checked-keys="[5]"></el-tree>
        </um-box>
      </template>
      <template v-slot:right>
        <um-tabs>
          <el-tabs v-model="tab">
            <el-tab-pane v-for="i in 5" :key="i" :name="`tab${i}`">
              <span slot="label">
                <um-icon name="list"></um-icon>
                Tab{{ i }}
              </span>
              <um-box>
                <p>这里是Tab{{ i }}</p>
              </um-box>
            </el-tab-pane>
          </el-tabs>
        </um-tabs>
      </template>
    </um-split>
  </um-container>
</template>
<script>
export default {
  data() {
    return {
      split: 0.2,
      tab: 'tab1',
      data: [
        {
          id: 1,
          label: '一级 2',
          children: [
            {
              id: 3,
              label: '二级 2-1',
              children: [
                {
                  id: 4,
                  label: '三级 3-1-1'
                },
                {
                  id: 5,
                  label: '三级 3-1-2',
                  disabled: true
                }
              ]
            },
            {
              id: 2,
              label: '二级 2-2',
              disabled: true,
              children: [
                {
                  id: 6,
                  label: '三级 3-2-1'
                },
                {
                  id: 7,
                  label: '三级 3-2-2',
                  disabled: true
                }
              ]
            }
          ]
        }
      ],
      defaultProps: {
        children: 'children',
        label: 'label'
      }
    }
  }
}
</script>
