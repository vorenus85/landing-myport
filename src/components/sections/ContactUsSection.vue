<template>
  <div class="contact-us-section">
    <div class="container mx-auto" id="contact-us">
      <div class="contact-us-module">
        <div class="module-head">
          <h2 class="module-title">{{ title }}</h2>
          <h3 class="module-subtitle">{{ subTitle }}</h3>
        </div>
        <div class="module-body">
          <a href="#">{{ cta }}</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { onMounted, ref } from 'vue'
import moduleData from '@/mock-data/contactUsSection.json'

const title = ref(null)
const subTitle = ref(null)
const cta = ref(null)

onMounted(() => {
  title.value = moduleData.data.title
  subTitle.value = moduleData.data.subTitle
  cta.value = moduleData.data.cta
})
</script>

<style lang="scss" scoped></style>
