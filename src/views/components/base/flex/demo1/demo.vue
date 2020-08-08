<template>
  <um-container>
    <um-split v-model="split">
      <template v-slot:left>
        <um-box page>
          <um-flex direction="row" fix-mode="left" height="500px" fix="150px">
            <template v-slot:left>
              <div class="page um-bg-success">
                <p class="um-text-whrite">这里宽度是固定的</p>
              </div>
            </template>
            <template v-slot:right>
              <div class="page um-bg-warning">
                <p class="um-text-whrite">
                  这里宽度是弹性的，这里宽度是弹性的，这里宽度是弹性的，这里宽度是弹性的，这里宽度是弹性的，这里宽度是弹性的，这里宽度是弹性的，这里宽度是弹性的，这里宽度是弹性的，这里宽度是弹性的，这里宽度是弹性的，这里宽度是弹性的
                </p>
              </div>
            </template>
          </um-flex>
        </um-box>
      </template>
      <template v-slot:right>
        <um-split v-model="split1" mode="vertical">
          <template v-slot:top>
            <um-box page no-scrollbar>
              <um-flex fix-mode="top" fix="150px">
                <template v-slot:top>
                  <div class="page um-bg-success">
                    <p class="um-text-whrite">这里宽度是固定的</p>
                  </div>
                </template>
                <template v-slot:bottom>
                  <div class="page um-bg-warning">
                    <p class="um-text-whrite">
                      这里宽度是弹性的，这里宽度是弹性的，这里宽度是弹性的，这里宽度是弹性的，这里宽度是弹性的，这里宽度是弹性的，这里宽度是弹性的，这里宽度是弹性的，这里宽度是弹性的，这里宽度是弹性的，这里宽度是弹性的，这里宽度是弹性的
                    </p>
                  </div>
                </template>
              </um-flex>
            </um-box>
          </template>
          <template v-slot:bottom>
            <um-box page />
          </template>
        </um-split>
      </template>
    </um-split>
  </um-container>
</template>
<script>
export default {
  data() {
    return {
      split: 0.5,
      split1: 0.5
    }
  }
}
</script>
