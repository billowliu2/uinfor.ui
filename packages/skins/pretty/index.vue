<template>
  <div class="um-wrapper">
    <um-header />
    <um-main />
  </div>
</template>
<script>
import NmHeader from './components/header'
import NmMain from './components/main'
export default {
  components: { NmHeader, NmMain }
}
</script>
<style lang="scss">
@import './styles/_index.scss';
</style>
