<script lang="ts" setup>
const { t } = useI18n()
const loginForm = ref({
  userAccount: '',
  userPassword: '',
})
const loginRules = ref({
  userAccount: [
    { required: true, message: t('systemLogin.userAccountMsg'), trigger: 'blur,change' },
  ],
  userPassword: [
    { required: true, message: t('systemLogin.userPasswordMsg'), trigger: 'blur,change' },
  ],
})
// const login = () => {
//   const { username, password } = loginForm
//   loginApi({ username, password }).then(res => {
//     const { data } = res
//     if (data.code === 200) {
//       const { token } = data.data
//       setToken(token)
//       router.push({ path: '/' })
//     }
//   })
// }
</script>

<template>
  <div h-screen w-screen>
    <div mx-auto h-full w-md flex items-center>
      <n-card hoverable>
        <n-form
          :model="loginForm"
          :rules="loginRules"
          label-placement="left"
          label-width="auto"
        >
          <n-form-item :label="$t('systemLogin.userAccount')" prop="userAccount">
            <n-input v-model="loginForm.userAccount" :placeholder="$t('systemLogin.userAccountMsg')" />
          </n-form-item>
          <n-form-item :label="$t('systemLogin.userPassword')" prop="userPassword">
            <n-input v-model="loginForm.userPassword" :placeholder="$t('systemLogin.userPasswordMsg')" />
          </n-form-item>
          <n-form-item>
            <n-button round type="info">
              {{ t('systemLogin.login') }}
            </n-button>
          </n-form-item>
        </n-form>
      </n-card>
    </div>
  </div>
</template>

<route lang="yaml">
meta:
layout: auth
</route>
