<script setup lang="ts">
import { ref } from 'vue'

defineProps<{
  name: string
  emoji: string
  imageSrc?: string
  fact: string
  habitat?: string
  type?: string
  accentColor?: string
}>()

const isFlipped = ref(false)
</script>

<template>
  <div
    class="animal-card-scene"
    @click="isFlipped = !isFlipped"
    role="button"
    :aria-label="`${name} - click to ${isFlipped ? 'hide' : 'reveal'} fact`"
    :aria-pressed="isFlipped"
  >
    <div class="animal-card" :class="{ 'is-flipped': isFlipped }">

      <!-- Front face -->
      <div
        class="animal-card-face animal-card-front"
        :style="{ borderColor: accentColor ?? '#FF6B6B' }"
      >
        <div class="animal-emoji">{{ emoji }}</div>
        <img
          v-if="imageSrc"
          :src="imageSrc"
          :alt="name"
          class="animal-image"
          @error="($event.target as HTMLImageElement).style.display = 'none'"
        />
        <h3 class="animal-name">{{ name }}</h3>
        <p v-if="type" class="animal-type">{{ type }}</p>
        <div class="flip-hint">👆 Tap me!</div>
      </div>

      <!-- Back face -->
      <div
        class="animal-card-face animal-card-back"
        :style="{ backgroundColor: accentColor ?? '#FF6B6B' }"
      >
        <div class="back-emoji">{{ emoji }}</div>
        <p class="animal-fact">{{ fact }}</p>
        <p v-if="habitat" class="animal-habitat">
          <strong>Home:</strong> {{ habitat }}
        </p>
        <div class="flip-hint">👆 Tap to flip back</div>
      </div>

    </div>
  </div>
</template>

<style scoped>
.animal-card-scene {
  width: 240px;
  height: 300px;
  perspective: 900px;
  cursor: pointer;
  flex-shrink: 0;
}

.animal-card {
  width: 100%;
  height: 100%;
  position: relative;
  transform-style: preserve-3d;
  -webkit-transform-style: preserve-3d;
  transition: transform 0.6s cubic-bezier(0.4, 0, 0.2, 1);
}

.animal-card-scene:hover .animal-card:not(.is-flipped) {
  transform: translateY(-6px) rotateY(8deg);
}

.animal-card.is-flipped {
  transform: rotateY(180deg);
}

.animal-card-face {
  position: absolute;
  inset: 0;
  border-radius: 24px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 20px 16px;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15);
  backface-visibility: hidden;
  -webkit-backface-visibility: hidden;
  user-select: none;
}

.animal-card-front {
  background: #ffffff;
  border: 4px solid;
}

.animal-card-back {
  transform: rotateY(180deg);
  color: #fff;
}

.animal-emoji {
  font-size: 4.5rem;
  line-height: 1;
  margin-bottom: 6px;
}

.animal-image {
  width: 72px;
  height: 72px;
  object-fit: cover;
  border-radius: 50%;
  margin-bottom: 6px;
}

.animal-name {
  font-size: 1.5rem;
  font-weight: 900;
  margin: 4px 0 2px;
  text-align: center;
  color: #333;
}

.animal-type {
  font-size: 0.8rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  opacity: 0.5;
  margin: 0;
}

.back-emoji {
  font-size: 3rem;
  margin-bottom: 10px;
}

.animal-fact {
  font-size: 0.95rem;
  font-weight: 700;
  text-align: center;
  line-height: 1.5;
  margin: 0 0 10px;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.2);
}

.animal-habitat {
  font-size: 0.8rem;
  margin: 0;
  opacity: 0.85;
  text-align: center;
}

.flip-hint {
  margin-top: auto;
  font-size: 0.7rem;
  opacity: 0.55;
  padding-top: 8px;
}
</style>
