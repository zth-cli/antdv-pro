<script setup lang="ts">
import { useLayoutState } from '~/layouts/basic-layout/context.ts'
const prefixCls = shallowRef('ant-pro-footer-toolbar')
const { siderWidth: layoutSiderWidth, mobileCollapsed } = useLayoutState()
defineOptions({
  name: 'FooterToolBar',
})
const barWidth = computed(() => {
  return mobileCollapsed ? undefined : `calc(100% - ${layoutSiderWidth.value}px)`
})
</script>

<template>
  <div :class="prefixCls" :style="{ width: barWidth, transition: '0.3s all' }">
    <div class="footer-tool-bar__left">
      <slot name="left" />
    </div>
    <div class="footer-tool-bar__center">
      <slot />
    </div>
    <div class="footer-tool-bar__right">
      <slot name="right" />
    </div>
  </div>
  <div class="h-56px" />
</template>

<style scoped lang="less">
@import "./index.less";

.footer-tool-bar__left {
  float: left;
}
.footer-tool-bar__right {
  float: right;
}
.footer-tool-bar__center {
  float: none;
}
</style>
