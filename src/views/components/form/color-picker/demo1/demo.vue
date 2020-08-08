<template>
  <um-box page>
    <el-row :gutter="20">
      <el-col :span="12">
        <um-box header title="基础用法" icon="edit">
          <el-row>
            <el-col :span="19" :offset="2">
              <um-form :model="model">
                <el-form-item label="普通用法：" prop="color">
                  <um-color-picker v-model="model.color" />
                </el-form-item>
                <el-form-item label="禁用：" prop="color1">
                  <um-color-picker v-model="model.color1" disabled />
                </el-form-item>
                <el-form-item label="透明度：" prop="color1">
                  <um-color-picker v-model="model.color2" show-alpha />
                </el-form-item>
                <el-form-item label="预定义颜色：" prop="color1">
                  <um-color-picker v-model="model.color2" :predefine="predefine" />
                </el-form-item>
              </um-form>
            </el-col>
          </el-row>
        </um-box>
      </el-col>
      <el-col :span="12"></el-col>
    </el-row>
  </um-box>
</template>
<script>
export default {
  data() {
    return {
      model: {
        color: '',
        color1: '',
        color2: ''
      },
      predefine: ['#ccc', '#744914', '#B80A04', '#808080']
    }
  }
}
</script>
<style></style>
