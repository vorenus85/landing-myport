<template>
  <section class="header-section">
    <HeaderTopModule></HeaderTopModule>
    <HeroModule></HeroModule>
  </section>
</template>

<script setup>
import HeaderTopModule from '../modules/HeaderTopModule.vue';
import HeroModule from '../modules/HeroModule.vue';
</script>

<style lang="scss" scoped>
.header-section {
  background: var(--secondary-color);
  padding: 55px 0;
}
</style>
