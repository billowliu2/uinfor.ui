<template>
  <um-box ref="page" page header class="um-listbox" :icon="icon">
    <template v-slot:header>
      <div class="um-box-header-icon">
        <um-icon v-if="icon" :name="icon" />
      </div>
      <div class="um-box-header-text">{{ title }}</div>
      <span v-if="!noCount" class="um-listbox-count">已选 {{ value.length }} 个</span>
    </template>

    <ul v-if="value && value.length > 0" class="um-listbox-list">
      <li class="um-listbox-item" v-for="item in value_" :key="item.value" :title="item.label">
        <slot :item="item">
          <span class="um-listbox-item-text">{{ item.label }}</span>
          <um-button class="um-listbox-delete" circle type="danger" icon="delete" @click="remove(item.value)" />
        </slot>
      </li>
    </ul>
    <p v-else class="no-data">无</p>
  </um-box>
</template>
<script>
export default {
  name: 'Listbox',
  data() {
    return {
      value_: this.value,
      resizeing: false
    }
  },
  props: {
    value: {
      type: Array,
      required: true
    },
    // 标题
    title: {
      type: String,
      default: '列表'
    },
    // 左侧图标
    icon: {
      type: String,
      default: 'select'
    },
    /** 不显示数量 */
    noCount: Boolean
  },
  methods: {
    remove(v) {
      this.value_.splice(
        this.value_.findIndex(item => item.value === v),
        1
      )
      this.$emit('input', this.value_)
      this.$emit('remove', v, this.value_)
    },
    scrollbarResize() {
      if (!this.resizeing) {
        this.resizeing = true
        setTimeout(() => {
          this.$nextTick(() => {
            this.$refs.page.scrollbarResize()
            this.resizeing = false
          })
        }, 300)
      }
    }
  },
  watch: {
    value(val) {
      this.value_ = val
      this.scrollbarResize()
    }
  }
}
</script>
