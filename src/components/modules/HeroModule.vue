<template>
  <div class="container mx-auto">
    <div class="hero-section">
      <div class="hero-top grid grid-cols-1 lg:grid-cols-2 gap-4">
        <div class="hero-title">
          <h1 v-html="heroTitle"></h1>
        </div>
        <div class="hero-description pl-0 lg:pl-20 pr-0 lg:pr-10">
          <p v-html="description" class="pb-5"></p>
          <a @click="showContactUs" class="hero-cta"> {{ cta }}</a>
        </div>
      </div>
      <div class="hero-image">
        <img
          :alt="banner.alt"
          :src="imageUrl(banner.image, folder)"
          fetchpriority="high"
          :width="banner.width"
          :height="banner.height"
        />
      </div>
    </div>
  </div>
</template>

<script setup>
import { onMounted, ref } from 'vue'
import { useImageUrl } from '../../composables/useImageUrl.js'
import moduleData from '../../mock-data/heroModule.json'
const folder = 'herobanner'
const { imageUrl } = useImageUrl()
const heroTitle = ref(null)
const description = ref(null)
const cta = ref(null)
const banner = ref({ alt: '', image: '' })

const showContactUs = () => {
  console.log('show contact us')
}

onMounted(() => {
  heroTitle.value = moduleData.data.title
  description.value = moduleData.data.description
  cta.value = moduleData.data.cta
  banner.value = moduleData.data.banner
})
</script>

<style lang="scss" scoped>
@import '@/assets/scss/_variables.scss';
@import '@/assets/scss/_fonts.scss';
.hero-title {
  @include playfair-display-700;
  font-size: 3rem;
  line-height: 3.5rem;
  color: #fff;

  @media (min-width: 1024px) {
    font-size: 64px;
    line-height: 96px;
  }
}

.hero-top {
  padding: 50px 0;
  @media (min-width: 1024px) {
    padding: 50px 0 100px 0;
  }
}

.hero-description {
  color: rgba(255, 255, 255, 0.7);
  font-size: 1rem;
  letter-spacing: 0.3px;
  line-height: 25px;
}

.hero-cta {
  cursor: pointer;
  padding-left: 20px;
  text-transform: uppercase;
  color: $primary-color;
  font-family: DM Sans;
  font-size: 12px;
  font-weight: 700;
  line-height: 30px;
  letter-spacing: 0.5em;
  text-align: left;
  text-decoration-style: solid;
  text-underline-position: from-font;
  text-decoration-skip-ink: none;
  position: relative;

  &:hover {
    padding-left: 0;
    padding-right: 20px;
    &:before {
      left: auto;
      right: -10px;
    }
  }

  &:before {
    content: '/';
    position: absolute;
    left: 0;
  }

  &:after {
    content: '';
    position: absolute;
    bottom: 0;
    left: 0;
    display: block;
    height: 1px;
    width: 100%;
    background: $primary-color;
  }
}

.hero-image {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: -180px;
}
</style>
