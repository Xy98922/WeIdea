<script setup lang="ts">
import { NConfigProvider } from 'naive-ui'
import { NaiveProvider } from '@/components/common'
import { useTheme } from '@/hooks/useTheme'
import { useLanguage } from '@/hooks/useLanguage'

const { theme } = useTheme()
const { language } = useLanguage()
const themeOverrides = {
  common: {
    primaryColor: '#1a4f99',
    primaryColorHover: '#1a4f99',
    primaryColorPressed: '#1a4f99',
  },
  Button: {
    textColor: '#1a4f99',
  },
}
</script>

<template>
  <NConfigProvider class="h-full" :theme="theme" :theme-overrides="themeOverrides" :locale="language">
    <NaiveProvider>
      <RouterView />
    </NaiveProvider>
  </NConfigProvider>
</template>

<style scoped>
.h-full {
  background-color: #ffffff;
  /* background-image: url("C:\Users\leoyangxiao\Desktop\chatgpt-web\public\3e426070d8a43772b8fc0c1d7e7bc3b.png"); */
}
</style>
