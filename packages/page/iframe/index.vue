<template>
  <um-container>
    <iframe :src="url" style="width:100%;height:100%" />
  </um-container>
</template>
<script>
export default {
  name: 'IframeMenu',
  computed: {
    url() {
      return decodeURI(this.$route.params.url)
    }
  }
}
</script>
