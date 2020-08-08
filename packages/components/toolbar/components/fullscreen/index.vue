<template>
  <div class="um-toolbar-item">
    <um-button class="um-toolbar-button" type="text" @click="toggle">
      <um-icon :name="icon" />
    </um-button>
  </div>
</template>

<script>
import { mapState, mapActions } from 'vuex'
export default {
  computed: {
    ...mapState('app/fullscreen', ['active']),
    icon() {
      return this.active ? 'fullscreen-c' : 'fullscreen-o'
    }
  },
  methods: {
    ...mapActions('app/fullscreen', ['toggle'])
  }
}
</script>
