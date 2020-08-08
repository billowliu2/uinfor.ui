<template>
  <um-box page header title="对话框表单示例">
    <um-button text="新增" @click="dialog.add = true" />
    <um-button text="编辑" @click="dialog.edit = true" />
    <um-form-dialog v-bind="dialogAdd" :visible.sync="dialog.add">
      <el-row>
        <el-col :span="21" :offset="1">
          <el-form-item label="姓名：" prop="name">
            <el-input v-model="dialogAdd.model.name" />
          </el-form-item>
        </el-col>
        <el-col :span="21" :offset="1">
          <el-form-item label="年龄：" prop="age">
            <el-input v-model="dialogAdd.model.age" />
          </el-form-item>
        </el-col>
      </el-row>
    </um-form-dialog>
    <um-form-dialog v-bind="dialogEdit" :visible.sync="dialog.edit">
      <el-row>
        <el-col :span="21" :offset="1">
          <el-form-item label="姓名：" prop="name">
            <el-input v-model="dialogEdit.model.name" />
          </el-form-item>
        </el-col>
        <el-col :span="21" :offset="1">
          <el-form-item label="年龄：" prop="age">
            <el-input v-model="dialogEdit.model.age" />
          </el-form-item>
        </el-col>
      </el-row>
    </um-form-dialog>
  </um-box>
</template>
<script>
export default {
  data() {
    return {
      dialog: {
        add: false,
        edit: false
      },
      dialogAdd: {
        header: true,
        title: '新增',
        icon: 'add',
        model: {
          name: '',
          age: 0
        },
        rules: {
          name: [{ required: true, message: '请输入姓名' }]
        },
        action() {
          return new Promise(resolve => {
            resolve()
          })
        }
      },
      dialogEdit: {
        header: true,
        title: '编辑',
        icon: 'edit',
        model: {
          name: '',
          age: 0
        },
        rules: {
          name: [{ required: true, message: '请输入姓名' }]
        },
        action() {
          return new Promise(resolve => {
            resolve()
          })
        }
      }
    }
  }
}
</script>
