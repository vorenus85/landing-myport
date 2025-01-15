<template>
  <div class="about-us-section">
    <div class="container mx-auto" id="about-us">
      <div class="about-us-module">
        <div class="module-head">
          <h2 class="module-title">{{ title }}</h2>
          <h3 class="module-subtitle">{{ subTitle }}</h3>
        </div>
        <div class="module-body">
          {{ description }}
        </div>
      </div>
      <div class="references-list">
        <div class="reference" v-for="reference in references" :key="reference.id">
          <div class="reference-image-wrapper">
            <div class="reference-image">{{ reference.image }}</div>
          </div>
          <div class="reference-name">{{ reference.title }}</div>
          <div class="reference-footer">
            <div class="reference-type">{{ reference.type }}</div>
            <div class="reference-url">{{ reference.url }}</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { onMounted, ref } from 'vue'
import moduleData from '../../mock-data/aboutUsSection.json'

const title = ref(null)
const subTitle = ref(null)
const description = ref(null)
const references = ref([])
onMounted(() => {
  title.value = moduleData.data.title
  subTitle.value = moduleData.data.subTitle
  description.value = moduleData.data.description
  references.value = moduleData.data.references
})
</script>

<style lang="scss" scoped>
.about-us-section {
  background: var(--secondary-color);
  padding: 55px 0;
}
</style>
