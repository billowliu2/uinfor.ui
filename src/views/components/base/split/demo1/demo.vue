<template>
  <um-split v-model="split">
    <template v-slot:left>
      <um-box page>左侧面板</um-box>
    </template>
    <template v-slot:right>
      <um-split v-model="split1" mode="vertical">
        <template v-slot:top>
          <um-box page>上方面板</um-box>
        </template>
        <template v-slot:bottom>
          <um-box page>下方面板</um-box>
        </template>
      </um-split>
    </template>
  </um-split>
</template>
<script>
export default {
  data() {
    return {
      split: 0.3,
      split1: 0.3
    }
  }
}
</script>
