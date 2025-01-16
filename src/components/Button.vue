<template>
  <div class="btn" :class="btnVariant">{{ label }}</div>
</template>

<script setup>
import { computed } from 'vue'

const props = defineProps({
  label: String,
  variant: {
    type: String,
    default: 'white',
    validator: value => {
      const available = ['white', 'primary', '']
      return available.includes(value)
    }
  }
})

const btnVariant = computed(() => {
  return 'btn-' + props.variant
})
</script>

<style lang="scss" scoped>
@import '@/assets/scss/_fonts.scss';
@import '@/assets/scss/_variables.scss';
.btn {
  @include poppins-700;
  font-size: 0.85rem;
  min-width: 148px;
  line-height: 48px;
  text-align: center;
  height: 48px;
  text-transform: uppercase;
  cursor: pointer;
  transition: all 0.2s;

  &:hover {
    opacity: 0.9;
  }

  &:active,
  &:focus {
    opacity: 0.8;
  }

  &-white {
    color: $secondary-color;
    background: #fff;
  }

  &-primary {
    color: #fff;
    background: $primary-color;
  }
}
</style>
