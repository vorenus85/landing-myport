<template>
  <section class="header-section relative">
    <HeaderTopModule class="relative z-10"></HeaderTopModule>
    <HeroModule></HeroModule>
    <img
      class="glow-right hidden lg:block"
      :src="imageUrl('glow_right.png', '')"
      width="429"
      height="553"
    />
    <img
      class="glow-left hidden lg:block"
      :src="imageUrl('glow_left.png', '')"
      width="369"
      height="743"
    />
  </section>
</template>

<script setup>
import HeaderTopModule from '../modules/HeaderTopModule.vue'
import HeroModule from '../modules/HeroModule.vue'
import { useImageUrl } from '@/composables/useImageUrl.js'
const { imageUrl } = useImageUrl()
</script>

<style lang="scss" scoped>
@import '@/assets/scss/_variables.scss';
.header-section {
  background: $secondary-color;
  padding: 55px 0;
}

.glow-right {
  position: absolute;
  top: 0;
  right: 0;
  z-index: 0;
}

.glow-left {
  position: absolute;
  bottom: -300px;
  left: 0;
  z-index: 0;
}
</style>
