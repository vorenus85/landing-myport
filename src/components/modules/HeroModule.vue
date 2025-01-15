<template>
  <div class="container mx-auto">
    <div class="hero-section">
      <div class="hero-top">
        <div class="hero-title">
          <h1 v-html="heroTitle"></h1>
        </div>
        <div class="hero-description">
          <p>
            We are a remote design agency based in Montreal, working with
            clients around the world. As passionate designers, we love building
            products that are easy to use, accessible, engaging, and delightful.
          </p>
          <a href="#contact-us" class="btn-link">Contact us</a>
        </div>
      </div>
      <div class="hero-image">
        <img
          :alt="banner.alt"
          :src="imageUrl(banner.image, folder)"
          fetchpriority="high"
        />
      </div>
    </div>
  </div>
</template>

<script setup>
import { onMounted, ref } from 'vue';
import { useImageUrl } from '../../composables/useImageUrl.js';
import moduleData from '../../mock-data/heroModule.json';
const folder = 'herobanner';
const { imageUrl } = useImageUrl();
const heroTitle = ref(null);
const description = ref(null);
const banner = ref({ alt: '', image: '' });

onMounted(() => {
  heroTitle.value = moduleData.data.title;
  description.value = moduleData.data.description;
  banner.value = moduleData.data.banner;
});
</script>

<style lang="scss" scoped></style>
