<template>
  <um-container>
    <demo />
    <um-code-preview :code="code" />
  </um-container>
</template>
<script>
import page from './page.js'
import Demo from './demo'
import code from '!!raw-loader!./demo'
export default {
  name: page.name,
  components: { Demo },
  data() {
    return {
      timer: null,
      code
    }
  },
  created() {
    this.setTabName('表单对话框示例代码')
  }
}
</script>
