<template>
  <div :class="classes">
    <div class="um-split-trigger-bar-con">
      <i class="um-split-trigger-bar" v-once v-for="i in 8" :key="`trigger-${i}`"></i>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    mode: String
  },
  data() {
    return {
      initOffset: 0
    }
  },
  computed: {
    isVertical() {
      return this.mode === 'vertical'
    },
    classes() {
      return ['um-split-trigger', this.isVertical ? `um-split-trigger-vertical` : `um-split-trigger-horizontal`]
    }
  }
}
</script>
