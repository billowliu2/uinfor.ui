<template>
  <um-container>
    <um-box page>
      <div class="um-error-403">
        <div class="um-error-403-number">
          <div>4</div>
          <div>0</div>
          <div>3</div>
        </div>
        <p class="um-m-10 um-size-60">ERROR !</p>
        <p class="um-m-20">亲！您无权访问该页面哦~</p>
        <p class="um-text-center"><um-button type="text" text="《 带您回家" @click="$router.push('/')" /> | <um-button type="text" text="原路返回 》" class="um-m-l-0" @click="$router.go(-1)" /></p>
      </div>
    </um-box>
  </um-container>
</template>
<style lang="scss">
.um-error-403 {
  margin: 100px auto;
  width: 600px;
  height: 400px;
  color: #979797;
  text-align: center;
  &-number {
    div {
      position: relative;
      display: inline-block;
      margin: 5px;
      width: 90px;
      height: 120px;
      line-height: 120px;
      text-align: center;
      font-size: 80px;
      border: 1px solid #cccccc;
      box-sizing: border-box;

      &::after {
        content: '';
        position: absolute;
        top: -4px;
        left: -4px;
        width: 96px;
        height: 126px;
        border: 1px solid #cccccc;
        box-sizing: border-box;
      }
    }
  }
}
</style>
