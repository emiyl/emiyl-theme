<script setup lang="ts">
import HomeContent from '@theme/HomeContent.vue'
import HomeFeatures from '@theme/HomeFeatures.vue'
import HomeFooter from '@theme/HomeFooter.vue'
import HomeHero from '@theme/HomeHero.vue'

import { useThemeLocaleData } from '@vuepress/theme-default/lib/client/composables'
const adUnits = useThemeLocaleData().value.adUnits
</script>

<template>
    <div class="hero">
        <HomeHero />
    </div>
    <main class="home">
        <HomeFeatures />
        <HomeContent />
        <template v-for="(unit, index) in adUnits" :key="unit">
            <div :id="`waldo-tag-${unit}`"></div>
            <hr v-if="index < adUnits.length"/>
        </template>
        <HomeFooter />
    </main>
</template>