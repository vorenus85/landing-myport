<template>
  <div class="services-section relative z-10 pb-10">
    <div class="container mx-auto" id="services">
      <div class="services-module pb-10 lg:px-10 lg:pt-10">
        <div class="module-head">
          <h2 class="module-title primary-color pb-5">{{ title }}</h2>
        </div>
        <div class="module-body grid grid-cols-1 lg:grid-cols-2 gap-4">
          <h3 class="module-subtitle">{{ subTitle }}</h3>
          <div class="module-description md:pt-3">{{ description }}</div>
        </div>
      </div>
      <div class="services-list grid grid-cols-1 md:grid-cols-3 gap-4 px-5 pt-10 lg:pt-2">
        <div class="service pb-5 px-5 lg:px-10" v-for="service in services" :key="service.id">
          <div class="service-icon-wrapper flex items-center justify-center">
            <div class="service-icon pb-5">
              <img
                :alt="service?.alt"
                :src="imageUrl(service?.icon, folder)"
                loading="lazy"
                :width="69"
                :height="69"
              />
            </div>
          </div>
          <div class="service-name text-center pb-5">{{ service.title }}</div>
          <div class="service-description text-center">{{ service.description }}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { onMounted, ref } from 'vue'
import moduleData from '@/mock-data/servicesSection.json'
import { useImageUrl } from '@/composables/useImageUrl.js'
const folder = 'services/'
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
@import '@/assets/scss/_fonts.scss';
@import '@/assets/scss/_variables.scss';
.services-section {
  padding-top: 80px;
}

.services-module {
  .module-title {
    text-transform: uppercase;
  }

  .module-subtitle {
    @include playfair-display-700;
    font-size: 24px;
    line-height: 32px;
    color: $secondary-color;
  }

  .module-body {
    line-height: 25.6px;
  }

  .module-description {
    color: rgba(34, 40, 49, 0.6);
    letter-spacing: 0.30000001192092896px;
    text-align: left;
  }
}

.services-list {
}

.service {
}

.service-name {
  @include dm-sans-700;
  font-size: 28px;
}

.service-description {
  color: #0f0b33b2;
  font-size: 1.25rem;
  line-height: 1.5;
}

@media (min-width: 1024px) {
  .services-section {
    padding-top: 180px;
  }

  .services-module {
    padding-bottom: 80px;

    .module-subtitle {
      @include playfair-display-700;
      font-size: 32px;
      line-height: 48px;
    }
  }
}
</style>
