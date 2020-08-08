<template>
  <um-box page>
    <um-button @click="drawer1 = true">简单抽屉</um-button>
    <um-button @click="drawer2 = true">左侧抽屉</um-button>
    <um-button @click="drawer3 = true">在附加到body</um-button>
    <um-button @click="drawer4 = true">可拖拽</um-button>
    <um-drawer header title="简单抽屉" :visible.sync="drawer1"></um-drawer>
    <um-drawer header title="左侧抽屉" placement="left" :visible.sync="drawer2"></um-drawer>
    <um-drawer header title="在附加到body" append-to-body :visible.sync="drawer3"></um-drawer>
    <um-drawer header title="可拖拽" draggable :visible.sync="drawer4"></um-drawer>
  </um-box>
</template>
<script>
export default {
  data() {
    return {
      drawer1: false,
      drawer2: false,
      drawer3: false,
      drawer4: false
    }
  }
}
</script>
