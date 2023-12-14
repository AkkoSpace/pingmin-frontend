<script lang="ts" setup>
import { ref } from 'vue'

const formData = ref({
  userAccount: '',
  userPassword: '',
})

function onSubmit() {}

function onReset() {}
</script>

<template>
  <div h-full w-full from-blue-200 to-green-200 bg-gradient-to-tr>
    <div h-screen flex items-center justify-center>
      <div

        h-30vh w-20vw flex items-center justify-center border-rd-2 bg-white p-2
      >
        <t-form
          :colon="true"
          :data="formData"
          :label-width="0"
          @reset="onReset"
          @submit="onSubmit"
        >
          <t-form-item name="userAccount">
            <t-input
              v-model="formData.userAccount"
              autocomplete="username"
              placeholder="请输入账号"
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
