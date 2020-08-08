<template>
  <section class="um-icon-picker">
    <div class="um-icon-picker-input">
      <el-input :placeholder="placeholder" v-model="icon" @change="onChange">
        <template v-slot:prepend>
          <um-icon :name="icon" />
        </template>
      </el-input>
    </div>
    <div class="um-icon-picker-button">
      <um-button icon="search" @click="panelVisible = true" />
    </div>
    <panel :visible.sync="panelVisible" @success="onSelect" />
  </section>
</template>
<script>
import Panel from './panel'
export default {
  name: 'IconPicker',
  components: { Panel },
  data() {
    return {
      icon: this.value,
      panelVisible: false
    }
  },
  props: {
    value: String,
    placeholder: String
  },
  methods: {
    onChange(val) {
      this.$emit('input', val)
    },
    onSelect(icon) {
      if (icon !== '') {
        this.icon = icon
        this.onChange(icon)
      }
    },
    reset() {
      this.icon = ''
      this.onChange('')
    }
  },
  watch: {
    value() {
      if (this.icon !== this.value) this.icon = this.value
    }
  }
}
</script>
