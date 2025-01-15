<template>
  <div class="our-teams-section">
    <div class="container mx-auto" id="our-teams">
      <div class="our-teams-module">
        <div class="module-head">
          <h2 class="module-title">{{ title }}</h2>
          <h3 class="module-subtitle">{{ subTitle }}</h3>
        </div>
        <div class="module-body">
          {{ description }}
        </div>
      </div>
      <div class="team-list">
        <div class="team-member" v-for="teamMember in team" :key="teamMember.id">
          <div class="team-member-image-wrapper">
            <div class="team-member-image">{{ teamMember.image }}</div>
          </div>
          <div class="team-member-name">{{ teamMember.name }}</div>
          <div class="team-member-role">{{ teamMember.role }}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { onMounted, ref } from 'vue'
import moduleData from '../../mock-data/ourTeamsSection.json'

const title = ref(null)
const subTitle = ref(null)
const description = ref(null)
const team = ref([])
onMounted(() => {
  title.value = moduleData.data.title
  subTitle.value = moduleData.data.subTitle
  description.value = moduleData.data.description
  team.value = moduleData.data.team
})
</script>

<style lang="scss" scoped></style>
