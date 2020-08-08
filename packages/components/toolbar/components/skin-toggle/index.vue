<template>
  <div class="um-toolbar-item">
    <um-button class="um-toolbar-button" type="text" @click="open">
      <um-icon name="skin" />
    </um-button>

    <toggle-form :visible.sync="visible" />
  </div>
</template>
<script>
import ToggleForm from './form'
export default {
  components: { ToggleForm },
  data() {
    return {
      visible: false
    }
  },
  methods: {
    open() {
      this.visible = true
    }
  }
}
</script>
