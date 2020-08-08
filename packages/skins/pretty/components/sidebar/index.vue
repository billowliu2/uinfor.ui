<template>
  <section class="um-sidebar" :class="{ collapse: collapse }">
    <section class="um-menu-wapper">
      <um-menus />
    </section>
  </section>
</template>
<script>
import NmMenus from '../menus'
import { mapState } from 'vuex'
export default {
  components: { NmMenus },
  computed: {
    ...mapState('app/skins/pretty/sidebar', ['collapse'])
  }
}
</script>
