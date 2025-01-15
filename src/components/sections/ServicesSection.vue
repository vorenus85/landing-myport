<template>
  <div class="services-section">
    <div class="container mx-auto" id="services">
      <div class="services-module grid grid-cols-1 lg:grid-cols-2 gap-4">
        <div class="module-head">
          <h2 class="module-title">{{ title }}</h2>
          <h3 class="module-subtitle">{{ subTitle }}</h3>
        </div>
        <div class="module-body">
          {{ description }}
        </div>
      </div>
      <div class="services-list grid grid-cols-1 md:grid-cols-3 gap-4">
        <div class="service" v-for="service in services" :key="service.id">
          <div class="service-icon-wrapper">
            <div class="service-icon">
              <img
                :alt="service.alt"
                :src="imageUrl(service.icon, folder)"
                loading="lazy"
                :width="69"
                :height="69"
              />
            </div>
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
import { useImageUrl } from '../../composables/useImageUrl.js'
const folder = 'services'
const { imageUrl } = useImageUrl()

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
