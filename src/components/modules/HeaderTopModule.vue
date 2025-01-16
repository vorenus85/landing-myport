<template>
  <div class="header-top">
    <div class="container mx-auto flex justify-between">
      <Logo />
      <HeaderMenu />
      <Button title="Get started"></Button>
    </div>
  </div>
</template>

<script setup>
import Button from '../Button.vue'
import HeaderMenu from './HeaderMenu.vue'
import Logo from '../Logo.vue'
</script>

<style lang="scss" scoped>
.header-top {
}
</style>
