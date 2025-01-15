<template>
  <div class="footer-section">
    <div class="container mx-auto">
      <Logo variant="dark" />
      <div class="contact-info contact-info-email">
        [icon] <a :href="`mailto:${email}`">{{ email }}</a>
      </div>
      <div class="contact-info contact-info-tel">
        [icon] <a :href="`tel:+${telNumber}`">{{ tel }}</a>
      </div>
    </div>
  </div>
</template>

<script setup>
import { computed, onMounted, ref } from 'vue'
import moduleData from '@/mock-data/footerData.json'
import Logo from '../Logo.vue'

const email = ref(null)
const tel = ref(null)

const telNumber = computed(() => {
  return tel.value?.replace(/[^0-9]+/g, '')
})

onMounted(() => {
  email.value = moduleData.data.email
  tel.value = moduleData.data.tel
})
</script>

<style lang="scss" scoped></style>
