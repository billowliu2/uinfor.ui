<template>
  <div class="um-toolbar">
    <template v-for="t in customToolbars">
      <component :key="t" :is="`um-toolbar-${t}`" />
    </template>
    <um-skin-toggle v-if="toolbar.skin" />
    <um-userinfo v-if="toolbar.userInfo" />
    <um-fullscreen v-if="toolbar.fullscreen" />
    <um-logout v-if="toolbar.logout" />
  </div>
</template>
<script>
import { mapState } from 'vuex'
import NmFullscreen from './components/fullscreen'
import NmLogout from './components/logout'
import NmSkinToggle from './components/skin-toggle'
import NmUserinfo from './components/userInfo'
export default {
  name: 'Toolbar',
  components: { NmFullscreen, NmLogout, NmSkinToggle, NmUserinfo },
  computed: {
    ...mapState('app/config', { toolbar: s => s.component.toolbar }),
    ...mapState('app/system', { customToolbars: s => s.customToolbars })
  }
}
</script>
