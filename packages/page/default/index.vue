<template>
  <um-container>
    <um-box page>
      <div class="um-default">
        <um-icon name="work" class="um-size-100" />
        <h1 class="um-m-20 um-size-20">欢迎登录{{ title }}~</h1>
        <p>本系统使用开源框架 <a class="um-link" target="_blank" href="https://github.com/iamoldli/NetModular">NetModular</a> 开发</p>
        <img style="width:100%" src="../../../public/images/motto.png" />
      </div>
    </um-box>
  </um-container>
</template>
<script>
import { mapState } from 'vuex'
export default {
  computed: {
    ...mapState('app/config', { title: s => s.system.title })
  }
}
</script>
<style lang="scss">
.um-default {
  margin: 100px auto;
  width: 600px;
  height: 400px;
  color: #979797;
  text-align: center;
}
</style>
