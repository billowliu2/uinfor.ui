<template>
  <section class="um-header">
    <section class="um-header-left">
      <!--Logo-->
      <section class="um-logo-box">
        <img :src="logoUrl" class="um-logo-img" :alt="title" :title="title" />
        <div class="um-logo-text">{{ title }}</div>
      </section>
      <!--折叠按钮-->
      <a class="um-sidebar-toggle-btn" @click.prevent="sidebarToggle">
        <um-icon :name="sidebarCollapse ? 'indent-left' : 'indent-right'" />
      </a>
      <!--面包屑-->
      <breadcrumb />
    </section>
    <section class="um-header-right">
      <!--工具栏-->
      <div class="um-header-toolbar">
        <um-toolbar />
      </div>
    </section>
  </section>
</template>
<script>
import { mapState, mapGetters, mapActions } from 'vuex'
import Breadcrumb from './components/breadcrumb'
export default {
  components: { Breadcrumb },
  computed: {
    ...mapGetters('app/config', ['logoUrl']),
    ...mapState('app/config', { title: s => s.system.title }),
    ...mapState('app/skins/pretty/sidebar', { sidebarCollapse: 'collapse' })
  },
  methods: {
    ...mapActions('app/skins/pretty/sidebar', { sidebarToggle: 'toggle' })
  }
}
</script>
