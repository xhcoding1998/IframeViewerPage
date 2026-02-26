<script setup lang="ts">
import HeroSection from './components/HeroSection.vue'
import FeaturesSection from './components/FeaturesSection.vue'
import InstallGuide from './components/InstallGuide.vue'
import FooterSection from './components/FooterSection.vue'
</script>

<template>
  <div class="app">
    <HeroSection />
    <FeaturesSection />
    <InstallGuide />
    <FooterSection />
  </div>
</template>

<style scoped>
.app {
  width: 100%;
}
</style>
