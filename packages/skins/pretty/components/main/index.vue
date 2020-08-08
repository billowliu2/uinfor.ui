<template>
  <section class="um-main">
    <div class="um-main-left">
      <um-sidebar />
    </div>
    <div class="um-main-right">
      <um-tabnav v-if="showTabnav" />
      <section class="um-content">
        <transition name="fade-transverse">
          <keep-alive v-if="showTabnav" :include="keepAlive">
            <router-view v-if="routerViewVisible" :key="$route.path" />
          </keep-alive>

          <router-view v-if="!showTabnav && routerViewVisible" :key="$route.path" />
        </transition>
      </section>
    </div>
  </section>
</template>
<script>
import NmSidebar from '../sidebar'
import { mapState, mapMutations } from 'vuex'
export default {
  components: { NmSidebar },
  data() {
    return {
      routerViewVisible: true
    }
  },
  computed: {
    ...mapState('app/page', ['keepAlive']),
    ...mapState('app/config', { showTabnav: s => s.component.tabnav.enabled })
  },
  provide() {
    return {
      reload: this.reload
    }
  },
  methods: {
    ...mapMutations('app/page', ['keepAliveRemove']),
    reload(name) {
      this.routerViewVisible = false
      this.keepAliveRemove(name)

      this.$nextTick(() => {
        this.routerViewVisible = true
      })
    }
  }
}
</script>
