<template>
  <div class="um-toolbar-item">
    <el-dropdown trigger="click">
      <um-button class="um-toolbar-button" type="text">
        <um-icon name="user" />
      </um-button>

      <el-dropdown-menu class="um-header-userinfo-dropdown" slot="dropdown">
        <el-dropdown-item>
          <um-button type="text" text="账户信息" icon="user" @click="openUserInfo" />
        </el-dropdown-item>
        <el-dropdown-item>
          <um-button type="text" text="修改密码" icon="password" @click="updatePassword.visiable = true" />
        </el-dropdown-item>
      </el-dropdown-menu>
    </el-dropdown>

    <!--修改密码-->
    <um-update-password :visible.sync="updatePassword.visiable" />
  </div>
</template>
<script>
import { mapState, mapGetters } from 'vuex'
import NmUpdatePassword from '../../../update-password'
export default {
  components: { NmUpdatePassword },
  data() {
    return {
      updatePassword: {
        visiable: false
      }
    }
  },
  computed: {
    ...mapState('app/account', { userName: 'name' }),
    ...mapGetters('app/config', ['userPage'])
  },
  methods: {
    openUserInfo() {
      this.$router.push({ name: this.userPage, query: { tn_: '账户信息' } })
    }
  }
}
</script>
