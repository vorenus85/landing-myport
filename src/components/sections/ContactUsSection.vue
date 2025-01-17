<template>
  <div class="contact-us-section">
    <div class="container mx-auto" id="contact-us">
      <div
        class="contact-us-module relative lazy-load-background"
        ref="observedElement"
        :style="{
          backgroundImage: isLoaded && currentBackgroundUrl ? `url(${currentBackgroundUrl})` : ''
        }"
      >
        <div class="contact-us-module-wrapper">
          <div class="module-head">
            <h2 class="module-title pb-5 lg:pb-10">/ {{ title }}</h2>
            <h3 class="module-subtitle lg:pt-5 pb-5 lg:pb-0">{{ subTitle }}</h3>
          </div>
          <div class="module-body pt-10 pb-10">
            <div class="contact-us-cta flex lg:mt-10">
              <a :href="`tel:+${telNumber}`" class="contact-us-cta-btn playfair-display-700"
                ><span>{{ cta }}</span></a
              >
              <img
                class="green-arrow ml-10"
                :src="imageUrl('green_arrow.svg', '')"
                width="88"
                height="66"
                alt="contact us"
              />
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { computed, onMounted, onUnmounted, ref } from 'vue'
import moduleData from '@/mock-data/contactUsSection.json'
import { useImageUrl } from '@/composables/useImageUrl.js'
import { useIntersectionObserver } from '@/composables/useIntersectionObserver'
const { imageUrl } = useImageUrl()

const title = ref(null)
const subTitle = ref(null)
const cta = ref(null)
const tel = ref(null)

const desktopBackgroundUrl = imageUrl('chair.webp', '') // Replace with desktop image path
const mobileBackgroundUrl = null // Replace with mobile image path

const currentBackgroundUrl = ref('')
const isLoaded = ref(false)

const telNumber = computed(() => {
  return tel.value?.replace(/[^0-9]+/g, '')
})

// Determine the background image based on screen width
const setResponsiveImage = () => {
  currentBackgroundUrl.value = window.matchMedia('(max-width: 1024px)').matches
    ? mobileBackgroundUrl
    : desktopBackgroundUrl
}

// Set up the composable for lazy loading
const { element: observedElement } = useIntersectionObserver(
  () => {
    isLoaded.value = true
  },
  { threshold: 0.1, once: true }
)

// Cleanup on component unmount
onUnmounted(() => {
  window.removeEventListener('resize', setResponsiveImage)
})

onMounted(() => {
  title.value = moduleData.data.title
  subTitle.value = moduleData.data.subTitle
  cta.value = moduleData.data.cta
  tel.value = moduleData.data.tel
  setResponsiveImage()
  window.addEventListener('resize', setResponsiveImage)
})
</script>

<style lang="scss" scoped>
@import '@/assets/scss/_variables.scss';
@import '@/assets/scss/_fonts.scss';

.contact-us-module {
  padding: 40px;
  background-color: $secondary-color;
  color: $primary-color;

  .module-title {
    @include montserrat-500;
    font-size: 12px;
    letter-spacing: 0.5em;
    text-transform: uppercase;
  }

  h3.module-subtitle {
    @include playfair-display-700;
    font-size: 32px;
    line-height: 1.5;
    color: #fff;
  }
}

.lazy-load-background {
  background-size: auto;
  background-position: calc(100% - 100px) 100%;
  background-repeat: no-repeat;
  transition: background-image 0.3s ease-in-out;
}

.contact-us-cta {
  font-size: 18px;
}

.contact-us-cta-btn {
  position: relative;
  z-index: 1;
  padding-left: 40px;
  transition: all 0.2s;

  &:hover {
    padding-right: 0.5rem;
    &:before {
      background: transparent;
      border: 1px solid #fff;
      transform-origin: center;
      transform: scale(1.5);
    }
  }

  span {
    position: relative;
    z-index: 1;
  }

  &:before {
    content: '';
    display: block;
    width: 66px;
    height: 66px;
    border-radius: 100%;
    background: #fff;
    border: 1px solid transparent;
    position: absolute;
    z-index: 0;
    top: calc(50% - 33px);
    left: 0;
    transition: all 0.2s;
  }
}

.green-arrow {
  max-width: 43px;
}

@media (min-width: 1024px) {
  .contact-us-module {
    padding: 80px;
  }

  .contact-us-module-wrapper {
    max-width: 550px;
  }

  .contact-us-module h3.module-subtitle {
    font-size: 45px;
    line-height: 72px;
  }

  .contact-us-cta {
    font-size: 32px;
  }

  .contact-us-cta-btn:before {
    width: 86px;
    height: 86px;
    top: calc(50% - 43px);
  }
}
</style>
