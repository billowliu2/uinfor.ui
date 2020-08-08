<template>
  <section :class="class_">
    <transition name="fade">
      <section class="um-drawer-modal" @click="onModalClick" v-if="modal" v-show="visible"></section>
    </transition>
    <transition :name="`move-${placement}`">
      <section
        ref="dialog"
        class="um-drawer-dialog"
        :style="{ width: wrapperWidth }"
        v-show="visible"
        v-loading="loading"
        :element-loading-text="loadingText"
        :element-loading-background="loadingBackground"
        :element-loading-spinner="loadingSpinner"
      >
        <!--头部-->
        <header v-if="header" class="um-drawer-header">
          <slot name="header">
            <div v-if="icon" class="um-drawer-header-icon">
              <um-icon v-if="icon" :name="icon" />
            </div>
            <!--标题-->
            <div class="um-drawer-header-title">{{ title }}</div>
            <!--工具栏-->
            <div class="um-drawer-header-toolbar">
              <!--工具栏插槽-->
              <slot name="toolbar" />

              <!--全屏按钮-->
              <um-button v-if="fullscreen" :icon="fullscreen_ ? 'min' : 'max'" @click="triggerFullscreen" />
              <!--关闭按钮-->
              <um-button icon="close" @click="close" />
            </div>
          </slot>
        </header>
        <section class="um-drawer-body">
          <section class="um-drawer-body-wrapper">
            <um-scrollbar v-if="!noScrollbar" ref="scrollbar" :horizontal="horizontal">
              <slot />
            </um-scrollbar>
            <slot v-else />
          </section>
        </section>
        <footer v-if="footer" class="um-drawer-footer">
          <slot name="footer"></slot>
        </footer>

        <!--拖拽按钮-->
        <div v-if="draggable" class="um-drawer-drag" :class="{ 'um-drawer-drag-left': placement === 'left' }" @mousedown="onTriggerMousedown">
          <slot name="trigger">
            <div class="um-drawer-drag-move-trigger">
              <div class="um-drawer-drag-move-trigger-point">
                <i></i>
                <i></i>
                <i></i>
                <i></i>
                <i></i>
              </div>
            </div>
          </slot>
        </div>
      </section>
    </transition>
  </section>
</template>
<script>
import { mapState } from 'vuex'
import { oneOf } from '../../utils/assist'
import { on, off } from '../../utils/dom'
export default {
  name: 'Drawer',
  data() {
    return {
      canMove: false,
      fullscreen_: false,
      wrapperWidth: this.width,
      minWidth: 226
    }
  },
  props: {
    /** 是否显示 */
    visible: Boolean,
    /** 是否显示头部 */
    header: Boolean,
    /** 是否显示底部 */
    footer: Boolean,
    /** 标题 */
    title: String,
    /** 图标 */
    icon: String,
    /** 位置 */
    placement: {
      type: String,
      default: 'right',
      validator(value) {
        return oneOf(value, ['left', 'right'])
      }
    },
    /** 宽度 */
    width: {
      type: String,
      default: '30%'
    },
    /** 是否显示水平滚动条 */
    horizontal: Boolean,
    /** loading */
    loading: Boolean,
    /** 是否附加到Body */
    appendToBody: Boolean,
    /** 是否显示模态框 */
    modal: {
      type: Boolean,
      default: true
    },
    /** 是否点击模态框关闭抽屉 */
    modalClickClose: {
      type: Boolean,
      default: true
    },
    /** 自定义class */
    customClass: String,
    /** 是否显示全屏按钮 */
    fullscreen: {
      type: Boolean,
      default: true
    },
    /** 没有内边距 */
    noPadding: Boolean,
    /** 可拖拽 */
    draggable: {
      type: Boolean,
      default: false
    },
    /** 不显示滚动条 */
    noScrollbar: Boolean
  },
  computed: {
    ...mapState('app/loading', { loadingText: 'text', loadingBackground: 'background', loadingSpinner: 'spinner' }),
    class_() {
      return ['um-drawer', this.placement, this.fullscreen_ ? 'fullscreen' : '', this.draggable ? 'draggable' : '', this.customClass, this.noPadding ? 'no-padding' : '', this.fontSize]
    }
  },
  methods: {
    append() {
      if (this.appendToBody) {
        // 附加到body下面
        document.body.appendChild(this.$el)
      }

      window.addEventListener('resize', this.resize)
    },
    close() {
      this.fullscreen_ = false
      this.$emit('update:visible', false)
    },
    resize() {
      this.$refs.scrollbar.update()
    },
    /** 开启全屏 */
    openFullscreen() {
      this.fullscreen_ = true
      // 全屏事件
      this.$emit('fullscreen-change', this.fullscreen_)
    },
    /** 关闭全屏 */
    closeFullscreen() {
      this.fullscreen_ = false
      // 全屏事件
      this.$emit('fullscreen-change', this.fullscreen_)
    },
    /** 全屏事件 */
    triggerFullscreen() {
      this.fullscreen_ ? this.closeFullscreen() : this.openFullscreen()
    },
    onModalClick() {
      if (this.modal && this.modalClickClose) {
        this.close()
      }
    },
    /** 拖拽按钮鼠标按下事件 */
    onTriggerMousedown() {
      if (!this.draggable) return
      this.canMove = true
      // 防止鼠标选中抽屉中文字，造成拖动trigger触发浏览器原生拖动行为
      window.getSelection ? window.getSelection().removeAllRanges() : document.selection.empty()
      on(document, 'mousemove', this.onMousemove)
      on(document, 'mouseup', this.onMouseup)
    },
    onMousemove(event) {
      if (!this.canMove || !this.draggable) return
      const { width, x } = this.$el.getBoundingClientRect()
      let wrapperWidth
      if (this.placement === 'right' && event.pageX - x > 20) {
        wrapperWidth = width + x - event.pageX
      } else if (this.placement === 'left' && event.pageX - x < width - 20) {
        wrapperWidth = event.pageX - x
      }
      if (wrapperWidth > this.minWidth) {
        this.wrapperWidth = wrapperWidth + 'px'
      }
    },
    onMouseup() {
      if (!this.draggable) return
      this.canMove = false
      off(document, 'mousemove', this.onMousemove)
      off(document, 'mouseup', this.onMouseup)
    }
  },
  mounted() {
    this.append()
  },
  destroyed() {
    off(document, 'mousemove', this.onMousemove)
    off(document, 'mouseup', this.onMouseup)
    if (this.$el && this.$el.parentNode) {
      this.$el.parentNode.removeChild(this.$el)
      window.removeEventListener('resize', this.resize)
    }
  },
  watch: {
    visible(val) {
      if (val) {
        this.$emit('open')

        this.$nextTick(() => {
          this.$emit('opened')
        })
      } else {
        this.$emit('close')

        this.$nextTick(() => {
          this.$emit('closed')
        })
      }
    }
  }
}
</script>
