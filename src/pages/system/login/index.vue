<script lang="ts" setup>
import { ref } from 'vue'
import { LockOnIcon, UserIcon } from 'tdesign-icons-vue-next'

const router = useRouter()

const formData = ref({
  userAccount: '',
  userPassword: '',
})

function onSubmit() {
  localStorage.setItem('userInfo', JSON.stringify(formData.value))
  // 跳转到首页
  router.push({ path: '/' })
}
</script>

<template>
  <div h-full w-full from-blue-200 to-green-200 bg-gradient-to-tr>
    <div h-screen flex items-center justify-center>
      <div
        h-30vh w-20vw flex items-center justify-center border-rd-2 bg-white p-4
      >
        <t-form
          :colon="true"
          :data="formData"
          :label-width="0"
          w-full
          @submit="onSubmit"
        >
          <t-form-item name="userAccount">
            <t-input
              v-model="formData.userAccount"
              autocomplete="username"
              clearable
              placeholder="请输入账号"
              w-full
            >
              <template #prefix-icon>
                <UserIcon />
              </template>
            </t-input>
          </t-form-item>

          <t-form-item name="userPassword">
            <t-input
              v-model="formData.userPassword"
              autocomplete="current-password"
              clearable
              placeholder="请输入密码"
              type="password"
            >
              <template #prefix-icon>
                <LockOnIcon />
              </template>
            </t-input>
          </t-form-item>

          <t-form-item>
            <t-button block shape="round" theme="primary" type="submit">
              登录
            </t-button>
          </t-form-item>
        </t-form>
      </div>
    </div>
  </div>
</template>

<route lang="yaml">
meta:
layout: auth
</route>
