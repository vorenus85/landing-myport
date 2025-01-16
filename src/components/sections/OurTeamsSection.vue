<template>
  <div class="our-teams-section">
    <div class="container mx-auto" id="our-teams">
      <div class="our-teams-module">
        <div class="module-head text-center pb-5">
          <h2 class="module-title">{{ title }}</h2>
        </div>
        <div class="module-body text-center pb-5 mx-auto">
          {{ description }}
        </div>
      </div>
      <div class="team-list pt-5 flex gap-8 items-start justify-center flex-wrap">
        <div class="team-member text-center" v-for="teamMember in team" :key="teamMember.id">
          <div class="team-member-image-wrapper">
            <div class="team-member-image pb-3">
              <img
                :alt="teamMember?.name"
                :src="imageUrl(teamMember?.image, folder)"
                loading="lazy"
                :width="155"
                :height="145"
              />
            </div>
          </div>
          <div class="team-member-name py-1">{{ teamMember.name }}</div>
          <div class="team-member-role py-1">{{ teamMember.role }}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { onMounted, ref } from 'vue'
import moduleData from '@/mock-data/ourTeamsSection.json'
import { useImageUrl } from '@/composables/useImageUrl.js'
const folder = 'teams/'
const { imageUrl } = useImageUrl()

const title = ref(null)
const description = ref(null)
const team = ref([])
onMounted(() => {
  title.value = moduleData.data.title
  description.value = moduleData.data.description
  team.value = moduleData.data.team
})
</script>

<style lang="scss" scoped>
@import '@/assets/scss/_fonts.scss';

.our-teams-section {
  padding: 50px 0;
}

.our-teams-module {
  .module-title {
    @include playfair-display-700;
    font-size: 32px;
  }

  .module-body {
    color: #22283199;
    line-height: 1.5;
    letter-spacing: 0.30000001192092896px;
  }
}

.team-member {
  &-name {
    line-height: 1.2;
    font-size: 20px;
    font-weight: 700;
  }

  &-role {
    line-height: 1.2;
  }
}

@media (min-width: 1024px) {
  .our-teams-section {
    padding: 100px 0;
  }

  .team-member {
    padding: 0 20px;
  }

  .our-teams-module .module-body {
    max-width: 625px;
  }

  .our-teams-module {
    .module-title {
      font-size: 50px;
      line-height: 1.5;
    }
  }
}
</style>
