<script lang="ts" setup>
defineOptions({
  name: 'IndexPage',
})
// const { t } = useI18n()
const router = useRouter()

// 从 localStorage 中获取用户信息
const userInfo = localStorage.getItem('userInfo')
if (!userInfo)
  router.push('/system/login')

const collapsed = ref(false)
function onCollapse(val: any) {
  collapsed.value = val
}
// function onClickMenuItem(key: any) {
//   console.log(key)
// }
</script>

<template>
  <div h-screen w-screen>
    <a-layout h-full class="layout">
      <a-layout-sider
        breakpoint="lg"
        :width="220"
        collapsible
        :collapsed="collapsed"
        @collapse="onCollapse"
      >
        <div class="logo" />
        <a-menu
          :default-open-keys="['1']"
          :default-selected-keys="['0_2']"
        >
          <!--          @menu-item-click="onClickMenuItem" -->
          <!--        > -->
          <a-menu-item key="0_1" disabled flex items-center>
            <!-- TODO 图标 -->
            Menu 1
          </a-menu-item>
          <a-menu-item key="0_2">
            <IconCalendar />
            Menu 2
          </a-menu-item>
          <a-sub-menu key="1">
            <template #title>
              <span><IconCalendar />Navigation 1</span>
            </template>
            <a-menu-item key="1_1">
              Menu 1
            </a-menu-item>
            <a-menu-item key="1_2">
              Menu 2
            </a-menu-item>
            <a-sub-menu key="2" title="Navigation 2">
              <a-menu-item key="2_1">
                Menu 1
              </a-menu-item>
              <a-menu-item key="2_2">
                Menu 2
              </a-menu-item>
            </a-sub-menu>
            <a-sub-menu key="3" title="Navigation 3">
              <a-menu-item key="3_1">
                Menu 1
              </a-menu-item>
              <a-menu-item key="3_2">
                Menu 2
              </a-menu-item>
              <a-menu-item key="3_3">
                Menu 3
              </a-menu-item>
            </a-sub-menu>
          </a-sub-menu>
          <a-sub-menu key="4">
            <template #title>
              <span><IconCalendar />Navigation 4</span>
            </template>
            <a-menu-item key="4_1">
              Menu 1
            </a-menu-item>
            <a-menu-item key="4_2">
              Menu 2
            </a-menu-item>
            <a-menu-item key="4_3">
              Menu 3
            </a-menu-item>
          </a-sub-menu>
        </a-menu>
      </a-layout-sider>
      <a-layout>
        <a-layout-header>
          <a-menu
            :open-keys="['1']"
            :selected-keys="['0_2']"
            mode="horizontal"
          >
            <a-menu-item key="0_1" disabled>
              Menu 1
            </a-menu-item>
            <a-menu-item key="0_2">
              <IconCalendar />
              Menu 2
            </a-menu-item>
            <a-sub-menu key="1">
              <template #title>
                <span><IconCalendar />Navigation 1</span>
              </template>
              <a-menu-item key="1_1">
                Menu 1
              </a-menu-item>
              <a-menu-item key="1_2">
                Menu 2
              </a-menu-item>
              <a-sub-menu key="2" title="Navigation 2">
                <a-menu-item key="2_1">
                  Menu 1
                </a-menu-item>
                <a-menu-item key="2_2">
                  Menu 2
                </a-menu-item>
              </a-sub-menu>
              <a-sub-menu key="3" title="Navigation 3">
                <a-menu-item key="3_1">
                  Menu 1
                </a-menu-item>
                <a-menu-item key="3_2">
                  Menu 2
                </a-menu-item>
                <a-menu-item key="3_3">
                  Menu 3
                </a-menu-item>
              </a-sub-menu>
            </a-sub-menu>
            <a-sub-menu key="4">
              <template #title>
                <span><IconCalendar />Navigation 4</span>
              </template>
              <a-menu-item key="4_1">
                Menu 1
              </a-menu-item>
              <a-menu-item key="4_2">
                Menu 2
              </a-menu-item>
              <a-menu-item key="4_3">
                Menu 3
              </a-menu-item>
            </a-sub-menu>
          </a-menu>
        </a-layout-header>
        <a-layout>
          <div mx-2 mt-4 h-full>
            <a-layout-content class="h-[calc(100%_-_48px)]">
              Content
            </a-layout-content>
            <a-layout-footer>Footer</a-layout-footer>
          </div>
        </a-layout>
      </a-layout>
    </a-layout>
  </div>
</template>

<route lang="yaml">
meta:
  layout: home
</route>

<style scoped>
.layout {
  background: var(--color-fill-2);
}
.layout :deep(.arco-layout-sider) .logo {
  height: 32px;
  margin: 12px 8px;
  background: rgba(255, 255, 255, 0.2);
}
.layout :deep(.arco-layout-sider-light) .logo {
  background: var(--color-fill-2);
}
.layout :deep(.arco-layout-header) {
  height: 64px;
  line-height: 64px;
  background: var(--color-bg-3);
}
.layout :deep(.arco-layout-footer) {
  height: 48px;
  color: var(--color-text-2);
  font-weight: 400;
  font-size: 14px;
  line-height: 48px;
}
.layout :deep(.arco-layout-content) {
  color: var(--color-text-2);
  font-weight: 400;
  font-size: 14px;
  background: var(--color-bg-3);
}
.layout :deep(.arco-layout-footer),
.layout :deep(.arco-layout-content) {
  display: flex;
  flex-direction: column;
  justify-content: center;
  color: var(--color-white);
  font-size: 16px;
  font-stretch: condensed;
  text-align: center;
}
</style>
