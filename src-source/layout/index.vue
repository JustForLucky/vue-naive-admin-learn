<template>
  <n-layout has-sider wh-full>
    <!-- 左侧菜单 -->
    <n-layout-sider
      bordered
      collapse-mode="width"
      :collapsed-width="64"
      :width="220"
      :native-scrollbar="false"
      :collapsed="appStore.collapsed"
    >
      <SideBar />
    </n-layout-sider>
    <!-- 右侧内容 -->
    <article flex-1 flex-col overflow-hidden>
      <!-- 头部 -->
      <header bg-white px-15 border-b bc-eee flex items-center :style="`height: ${header.height}px`">
        <AppHeader />
      </header>
      <!-- 页面导航栏 -->
      <section v-if="tags.visible" border-b bc-eee>
        <AppTags :style="{ height: `${tags.height}px` }" />
      </section>
      <!-- 主要页面内容 -->
      <section flex-1 overflow-hidden>
        <AppMain />
      </section>
    </article>
  </n-layout>
</template>

<script setup>
import AppHeader from './components/header/index.vue'
import SideBar from './components/sidebar/index.vue'
import AppMain from './components/AppMain.vue'
import AppTags from './components/tags/index.vue'
import { useAppStore } from '@/store'
import { header, tags } from '~/settings'

const appStore = useAppStore()
</script>
