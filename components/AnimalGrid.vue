<script setup lang="ts">
import AnimalCard from './AnimalCard.vue'

interface AnimalDatum {
  name: string
  emoji: string
  imageSrc: string
  fact: string
  habitat: string
  type: string
  accentColor: string
}

const ANIMAL_DATA: Record<string, AnimalDatum> = {
  kangaroo: {
    name: 'Kangaroo',
    emoji: '🦘',
    imageSrc: '/animals/kangaroo.png',
    fact: 'Kangaroos can jump 9 metres in a single bound and reach speeds of 70 km/h!',
    habitat: 'Grasslands & Outback',
    type: 'Marsupial',
    accentColor: '#FF6B6B',
  },
  koala: {
    name: 'Koala',
    emoji: '🐨',
    imageSrc: '/animals/koala.png',
    fact: 'Koalas eat only eucalyptus leaves and sleep up to 22 hours a day!',
    habitat: 'Eucalyptus forests',
    type: 'Marsupial',
    accentColor: '#95E1D3',
  },
  platypus: {
    name: 'Platypus',
    emoji: '🦫',
    imageSrc: '/animals/platypus.png',
    fact: 'The platypus has a duck bill, beaver tail, otter feet — and lays eggs!',
    habitat: 'Rivers & streams',
    type: 'Monotreme',
    accentColor: '#F38181',
  },
  wombat: {
    name: 'Wombat',
    emoji: '🐾',
    imageSrc: '/animals/wombat.png',
    fact: 'Wombats have backwards pouches so dirt doesn\'t get in when they dig tunnels!',
    habitat: 'Forests & grasslands',
    type: 'Marsupial',
    accentColor: '#A8E6CF',
  },
  echidna: {
    name: 'Echidna',
    emoji: '🦔',
    imageSrc: '/animals/echidna.png',
    fact: 'Echidnas have no teeth — they use a long sticky tongue to catch ants and termites!',
    habitat: 'Forests, deserts, mountains',
    type: 'Monotreme',
    accentColor: '#FFD93D',
  },
  kookaburra: {
    name: 'Kookaburra',
    emoji: '🐦',
    imageSrc: '/animals/kookaburra.png',
    fact: 'Kookaburras are kingfishers that laugh to mark their territory. You can hear them a km away!',
    habitat: 'Eucalyptus woodlands',
    type: 'Bird',
    accentColor: '#6BCB77',
  },
}

const props = withDefaults(
  defineProps<{
    animals: string[]
    columns?: number
  }>(),
  { columns: undefined }
)

const cols = props.columns ?? props.animals.length
</script>

<template>
  <div
    class="animal-grid"
    :style="{ gridTemplateColumns: `repeat(${cols}, auto)` }"
  >
    <AnimalCard
      v-for="key in animals"
      :key="key"
      v-bind="ANIMAL_DATA[key]"
    />
  </div>
</template>

<style scoped>
.animal-grid {
  display: grid;
  gap: 2.5rem;
  justify-content: center;
  align-items: center;
  padding: 1rem;
  width: 100%;
}
</style>
