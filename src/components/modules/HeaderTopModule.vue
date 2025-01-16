<template>
  <div class="header-top">
    <div class="container mx-auto flex justify-between">
      <Logo />
      <HeaderMenu />
      <Button label="Get started" @click="getStarted"></Button>
    </div>
  </div>
</template>

<script setup>
import Button from '../Button.vue'
import HeaderMenu from './HeaderMenu.vue'
import Logo from '../Logo.vue'

const getStarted = () => {
  document.getElementById('services').scrollIntoView({ behavior: 'smooth' })
}
</script>
