<template>
  <um-container>
    <um-box class="um-tmpl" page header :title="title" :icon="icon">
      <div>
        <slot />
      </div>
      <um-attributes v-if="attrs" :data="attrs" />
      <div>
        <slot name="after-attrs" />
      </div>
      <um-slots v-if="slots" :data="slots" />
      <div>
        <slot name="after-slots" />
      </div>
      <um-methods v-if="methods" :data="methods" />
      <div>
        <slot name="after-methods" />
      </div>
      <um-events v-if="events" :data="events" />
      <div>
        <slot name="after-events" />
      </div>
    </um-box>
  </um-container>
</template>
<script>
import NmAttributes from './components/attributes'
import NmMethods from './components/methods'
import NmEvents from './components/events'
import NmSlots from './components/slots'
export default {
  name: 'Tmpl',
  components: { NmAttributes, NmMethods, NmEvents, NmSlots },
  props: {
    title: {
      type: String
    },
    icon: {
      type: String
    },
    attrs: {
      type: Array
    },
    slots: {
      type: Array
    },
    methods: {
      type: Array
    },
    events: {
      type: Array
    }
  }
}
</script>
<style lang="scss">
.um-tmpl {
  &-box {
    margin-bottom: 30px;
    &-title {
      margin: 10px 0;
      font-size: 25px;
    }
  }
  .el-alert__title {
    font-size: 17px;
  }

  .el-alert__description {
    margin-top: 10px;
    font-size: 15px;
    p {
      margin-bottom: 10px;
    }
  }
}
</style>
