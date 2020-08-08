<template>
  <section class="um-container" :class="{ 'is-horizontal': horizontal }">
    <section class="um-container-main">
      <um-scrollbar v-if="scrollbar" :horizontal="horizontal">
        <slot />
      </um-scrollbar>
      <slot v-else />
    </section>
  </section>
</template>
<script>
export default {
  name: 'Container',
  props: {
    /** 滚动条 */
    scrollbar: Boolean,
    /** 是否显示水平滚动条 */
    horizontal: Boolean
  }
}
</script>
