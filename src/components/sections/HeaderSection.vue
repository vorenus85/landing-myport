<template>
  <section class="header-section">
    <HeaderTopModule></HeaderTopModule>
    <HeroModule></HeroModule>
  </section>
</template>

<script setup>
import HeaderTopModule from '../modules/HeaderTopModule.vue'
import HeroModule from '../modules/HeroModule.vue'
</script>

<style lang="scss" scoped>
@import '@/assets/scss/_variables.scss';
.header-section {
  background: $secondary-color;
  padding: 55px 0;
}
</style>
