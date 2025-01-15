<template>
  <div class="header-menu-module hidden lg:block">
    <ul class="header-menu flex">
      <li v-for="item in menu" :key="item.id">
        <a :href="item.href" class="header-menu-item">{{ item.title }}</a>
      </li>
    </ul>
  </div>
</template>

<script setup>
import moduleData from '../../mock-data/headerMenu.json'
import { onMounted, ref } from 'vue'

const menu = ref([])

onMounted(() => {
  menu.value = moduleData.data
})
</script>

<style lang="scss" scoped>
@import '@/assets/scss/_variables.scss';
.header-menu {
  gap: 10px;
  font-size: 0.875rem;
  text-transform: uppercase;
  color: #fff;

  &-item {
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 0.5rem 1rem;
    &:hover {
      color: $primary-color;
    }
  }
}
</style>
