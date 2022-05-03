<script setup lang="ts">
import PageMeta from '@theme/PageMeta.vue'
import PageNav from '@theme/PageNav.vue'

import { usePageData, usePageFrontmatter } from '@vuepress/client'
import type { DefaultThemePageFrontmatter } from '@vuepress/theme-default/lib/shared'
const frontmatter = usePageFrontmatter<DefaultThemePageFrontmatter>()

const pageTitle = frontmatter.value.title
const chartType = frontmatter.value.chartType || ''
const widePage = frontmatter.value.widePage || false
</script>

<template>
  <main class="page">
    <div :class="widePage ? 'home' : 'theme-default-content'">
      <slot name="top" />

      <Content v-if="!chartType" />
      <template v-else>
        <firmwareVersion v-if="chartType == 'firmwareVersion'"/>
        <jailbreak v-else-if="chartType == 'jailbreak'"/>
        <device v-else-if="chartType == 'device'"/>
        <deviceList v-else-if="chartType == 'deviceList'"/>
        <deviceGroupList v-else-if="chartType == 'deviceGroupList'"/>
        <deviceGroup v-else-if="chartType == 'deviceGroup'"/>
      </template>
    </div>

    <PageMeta />

    <PageNav />

    <slot name="bottom" />
  </main>
</template>
