<template>
  <div class="header-menu">
    <ul>
      <li v-for="item in menu" :key="item.id">
        <a :href="item.href">{{ item.title }}</a>
      </li>
    </ul>
  </div>
</template>

<script setup>
import menuItems from '../../mock-data/headerMenu.json';
import { onMounted, ref } from 'vue';

const menu = ref([]);

onMounted(() => {
  menu.value = menuItems.data;
});
</script>

<style lang="scss" scoped></style>
