<template>
  <div class="services-section">
    <div class="container mx-auto" id="services">
      <div class="services-module">
        <div class="module-head">
          <h2 class="module-title">{{ title }}</h2>
          <h3 class="module-subtitle">{{ subTitle }}</h3>
        </div>
        <div class="module-body">
          {{ description }}
        </div>
      </div>
      <div class="services-list">
        <div class="service" v-for="service in services" :key="service.id">
          <div class="service-icon-wrapper">
            <div class="service-icon">{{ service.icon }}</div>
          </div>
          <div class="service-name">{{ service.title }}</div>
          <div class="service-description">{{ service.description }}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { onMounted, ref } from 'vue'
import moduleData from '../../mock-data/servicesSection.json'

const title = ref(null)
const subTitle = ref(null)
const description = ref(null)
const services = ref([])
onMounted(() => {
  title.value = moduleData.data.title
  subTitle.value = moduleData.data.subTitle
  description.value = moduleData.data.description
  services.value = moduleData.data.services
})
</script>

<style lang="scss" scoped>
.services-section {
  padding-top: 180px;
}
</style>
