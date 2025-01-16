<template>
  <div class="footer-section">
    <div class="container mx-auto">
      <div class="footer-module flex items-center flex-col md:flex-row">
        <Logo variant="dark" class="footer-logo m-3 md:mr-auto" />
        <div class="contact-info contact-info-email p-2 lg:pr-3">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="20"
            height="16"
            viewBox="0 0 20 16"
            fill="none"
          >
            <path
              d="M18 0H2C1.46957 0 0.960859 0.210714 0.585786 0.585786C0.210714 0.960859 0 1.46957 0 2V14C0 14.5304 0.210714 15.0391 0.585786 15.4142C0.960859 15.7893 1.46957 16 2 16H18C18.5304 16 19.0391 15.7893 19.4142 15.4142C19.7893 15.0391 20 14.5304 20 14V2C20 1.46957 19.7893 0.960859 19.4142 0.585786C19.0391 0.210714 18.5304 0 18 0ZM18 4.7L10 10.034L2 4.7V2.297L10 7.63L18 2.297V4.7Z"
              fill="#222831"
            />
          </svg>
          <a :href="`mailto:${email}`">{{ email }}</a>
        </div>
        <div class="contact-info contact-info-tel p-2 lg:pl-3">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="18"
            height="18"
            viewBox="0 0 18 18"
            fill="none"
          >
            <path
              d="M17.487 14.14L13.422 10.444C13.2299 10.2693 12.9774 10.1762 12.7178 10.1842C12.4583 10.1922 12.212 10.3008 12.031 10.487L9.63804 12.948C9.06204 12.838 7.90404 12.477 6.71204 11.288C5.52004 10.095 5.15904 8.934 5.05204 8.362L7.51104 5.968C7.69745 5.78712 7.80617 5.54082 7.8142 5.2812C7.82223 5.02159 7.72892 4.76904 7.55404 4.57699L3.85904 0.512995C3.68408 0.320352 3.44092 0.203499 3.18119 0.187255C2.92146 0.17101 2.66564 0.256653 2.46804 0.425995L0.298038 2.28699C0.125149 2.46051 0.0219574 2.69145 0.00803782 2.93599C-0.00696218 3.18599 -0.292962 9.108 4.29904 13.702C8.30504 17.707 13.323 18 14.705 18C14.907 18 15.031 17.994 15.064 17.992C15.3086 17.9783 15.5394 17.8747 15.712 17.701L17.572 15.53C17.7421 15.333 17.8283 15.0774 17.8124 14.8177C17.7966 14.558 17.6798 14.3148 17.487 14.14Z"
              fill="#222831"
            />
          </svg>
          <a :href="`tel:+${telNumber}`">{{ tel }}</a>
        </div>
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

<style lang="scss" scoped>
@import '@/assets/scss/_variables.scss';
.footer-section {
  padding: 40px 0;
}

.contact-info {
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: 500;
  font-size: 0.85rem;

  svg {
    margin-right: 1rem;
  }

  a:hover {
    color: $primary-color;
  }
}
</style>
