<template>
  <NConfigProvider :theme="isDark ? darkTheme : null">
    <NuxtLink to="/">返回index</NuxtLink>
    <div>进入这个页面后手动刷新一下后可以看到部分组件存在主题不准确问题，（可能不止这几个组件，只有一开始进来才会，刷新可以触发）</div>
    <NButton type="primary" @click="isDark = !isDark">切换主题（切换完后又正常了）</NButton>
    <n-space>
      <n-alert title="Info 类型" type="info">Gee it's good to be back home</n-alert>
      <n-alert title="Success 类型" type="success">
        Leave it till tomorrow to unpack my case
      </n-alert>
      <n-button>Default</n-button>
      <n-button type="tertiary">Tertiary</n-button>
      <n-button type="primary">Primary</n-button>
      <n-button type="info">Info</n-button>
      <n-button type="success">Success</n-button>
      <n-button type="warning">Warning</n-button>
      <n-button type="error">Error</n-button>
    </n-space>
    <n-global-style />
  </NConfigProvider>
</template>

<script setup lang="ts">
  import { darkTheme, useOsTheme } from 'naive-ui';
  // 不止是获取系统主题会出现这个情况，如果我把这个值存到pinia，在每次进来获取也会触发，或者是使用vueuse的获取系统主题也同样会发生
  const osTheme = useOsTheme();
  const isDark = ref(osTheme.value && true);
</script>

<style scoped lang="scss"></style>
