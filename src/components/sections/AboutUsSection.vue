<template>
  <div class="about-us-section relative">
    <div class="container mx-auto relative z-10" id="about-us">
      <div class="about-us-module grid grid-cols-1 lg:grid-cols-2 gap-8">
        <div class="about-us-content lg:pr-10">
          <div class="module-head">
            <h2 class="module-title primary-color pb-5">{{ title }}</h2>
            <h3 class="module-subtitle pb-5">{{ subTitle }}</h3>
          </div>
          <div class="module-body pb-5 lg:pr-5">
            <div class="module-description pb-5" v-html="description"></div>
            <div class="module-footer flex mt-5">
              <Button variant="primary" label="Hire us" class="hire-us" />
            </div>
          </div>
        </div>
        <div class="about-us-video-container relative">
          <div class="about-us-video">
            <img
              alt="about us video"
              :src="imageUrl('video_cover.jpg', '')"
              loading="lazy"
              :width="628"
              :height="450"
            />
          </div>
          <div class="video-play-btn absolute z-10">
            <img
              alt="play video"
              :src="imageUrl('play.png', '')"
              loading="lazy"
              :width="84"
              :height="84"
            />
          </div>
        </div>
      </div>
    </div>
    <div class="references-list relative z-10 pt-10 mt-10">
      <Carousel v-bind="carouselConfig" ref="carouselRef">
        <Slide class="reference" v-for="reference in references" :key="reference.id">
          <div class="reference-card cursor" @click="showReference(reference.url)">
            <div class="reference-image-wrapper mb-3">
              <img
                class="reference-image"
                :alt="reference.alt"
                :src="imageUrl(reference.image, folder)"
                loading="lazy"
                :width="324"
                :height="191"
              />
            </div>
            <div class="reference-name">{{ reference.title }}</div>
            <div class="reference-footer">
              <div class="reference-type">{{ reference.type }}</div>
              <div class="reference-url">
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  width="18"
                  height="18"
                  viewBox="0 0 18 18"
                  fill="none"
                >
                  <path
                    d="M14.1698 15.9042L17.5026 15.9042L17.5026 0.0956625L1.69407 0.0956632L1.69407 3.42849L11.8128 3.42849L0.51556 14.7257L2.87258 17.0827L14.1698 5.78551L14.1698 15.9042Z"
                    fill="white"
                  />
                </svg>
              </div>
            </div>
          </div>
        </Slide>
      </Carousel>
    </div>
    <img
      class="about-us-glow absolute hidden lg:block"
      alt="glowing effect"
      :src="imageUrl('about_us_glow.png', '')"
      loading="lazy"
      :width="449"
      :height="743"
    />
  </div>
</template>

<script setup>
// If you are using PurgeCSS, make sure to whitelist the carousel CSS classes
import 'vue3-carousel/dist/carousel.css'
import { Carousel, Slide } from 'vue3-carousel'

import { onMounted, ref } from 'vue'
import moduleData from '@/mock-data/aboutUsSection.json'
import { useImageUrl } from '@/composables/useImageUrl.js'
import Button from '../Button.vue'
const folder = 'references/'
const { imageUrl } = useImageUrl()

const title = ref(null)
const subTitle = ref(null)
const description = ref(null)
const references = ref([])

const carouselRef = ref()

const carouselConfig = {
  itemsToShow: 1.5,
  itemsToScroll: 1,
  wrapAround: true,
  snapAlign: 'center',
  // breakpoints are mobile first
  // any settings not specified will fallback to the carousel settings
  breakpoints: {
    // 200px and up
    576: {
      itemsToShow: 1.5
    },
    // 400px and up
    768: {
      itemsToShow: 2.5
    },
    992: {
      itemsToShow: 3.5
    }
  }
}

const showReference = url => {
  window.open(url)
}

onMounted(() => {
  title.value = moduleData.data.title
  subTitle.value = moduleData.data.subTitle
  description.value = moduleData.data.description
  references.value = moduleData.data.references
})
</script>

<style lang="scss" scoped>
@import '@/assets/scss/_variables.scss';
@import '@/assets/scss/_fonts.scss';
.about-us-section {
  background: $secondary-color;
  padding: 40px 0;
}

.about-us-module {
  .module-title {
    @include poppins-700;
  }

  .module-subtitle {
    @include playfair-display-700;
    font-size: 24px;
    line-height: 1.5;
    color: #fff;
  }

  .module-description {
    color: #fff;
    opacity: 0.7;
    line-height: 1.5;
    letter-spacing: 0.30000001192092896px;
  }
}

.hire-us {
  font-size: 14px;
}

.about-us-glow {
  top: 50%;
  left: 0;
  transform: translate(-0, -50%);
}

.video-play-btn {
  // todo simple pulse effect
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  cursor: pointer;
}

.reference {
  &-card {
    cursor: pointer;
    display: flex;
    flex-direction: column;
    padding: 20px;
    border: 1px solid rgba(255, 255, 255, 0.15);
    transition: all 0.2s;

    &:hover {
      border: 1px solid $primary-color;
    }
  }

  &-name {
    @include montserrat-600;
    padding: 5px 0;
    font-size: 1rem;
    color: #fff;
    text-align: left;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }

  &-footer {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  &-type {
    @include montserrat-500;
    color: rgba(255, 255, 255, 0.7);
    font-size: 0.75rem;
  }

  &.carousel__slide {
    padding: 0 10px;
  }
}

@media (min-width: 1024px) {
  .about-us-section {
    padding: 120px 0;
  }

  .reference-name {
    font-size: 26px;
  }

  .reference.carousel__slide {
    padding: 0 29px;
  }
}
</style>
