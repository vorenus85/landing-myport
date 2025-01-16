<script setup>
import AboutUsSection from './components/sections/AboutUsSection.vue'
import ContactUsSection from './components/sections/ContactUsSection.vue'
import FooterSection from './components/sections/FooterSection.vue'
import HeaderSection from './components/sections/HeaderSection.vue'
import OurTeamsSection from './components/sections/OurTeamsSection.vue'
import ServicesSection from '@/components/sections/ServicesSection.vue'
</script>

<template>
  <HeaderSection /> <ServicesSection /> <AboutUsSection /><OurTeamsSection />
  <ContactUsSection /><FooterSection />
</template>
<style lang="scss">
@import '@/assets/scss/_variables.scss';
@import '@/assets/scss/_fonts.scss';
body {
  @include dm-sans-400;
  color: $secondary-color;
}
</style>
