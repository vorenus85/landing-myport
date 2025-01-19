<template>
  <a :href="baseUrl" class="logo flex items-center" :class="logoVariant" title="Home">
    <svg
      xmlns="http://www.w3.org/2000/svg"
      width="28"
      height="28"
      viewBox="0 0 28 28"
      fill="none"
      class="logo-icon"
    >
      <path d="M0 0L28 28V0H0Z" fill="#00D0B0" />
    </svg>
    <span class="logo-text">Myport</span>
  </a>
</template>

<script setup>
import { computed } from 'vue'

const baseUrl = import.meta.env.VITE_BASE_URL

const props = defineProps({
  variant: {
    type: String,
    default: 'light',
    validator: value => {
      const available = ['light', 'dark', '']
      return available.includes(value)
    }
  }
})

const logoVariant = computed(() => {
  return 'variant-' + props.variant
})
</script>

<style lang="scss" scoped>
@import '@/assets/scss/_fonts.scss';
@import '@/assets/scss/_variables.scss';
.logo {
  gap: 10px;
  font-size: 1rem;
  line-height: 1.5;
}

.variant {
  &-light {
    color: #fff;
  }

  &-dark {
    color: $secondary-color;
  }
}

.logo-text {
  @include dm-sans-700;
}
</style>
