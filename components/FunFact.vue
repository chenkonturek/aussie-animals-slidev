<script setup lang="ts">
defineProps<{
  emoji: string
  fact: string
  color?: string
}>()
</script>

<template>
  <div class="fun-fact-card" :style="{ backgroundColor: color ?? '#FFE66D' }">
    <div class="fun-fact-emoji">{{ emoji }}</div>
    <p class="fun-fact-text">{{ fact }}</p>
    <div class="fun-fact-label">Did you know? 🤩</div>
  </div>
</template>

<style scoped>
.fun-fact-card {
  border-radius: 20px;
  padding: 1.5rem 1.25rem;
  text-align: center;
  animation: bounce-in 0.5s cubic-bezier(0.68, -0.55, 0.265, 1.55) both;
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.12);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
  height: 100%;
}

.fun-fact-emoji {
  font-size: 3rem;
  line-height: 1;
}

.fun-fact-text {
  font-size: 0.95rem;
  font-weight: 700;
  line-height: 1.5;
  color: #333;
  margin: 0;
  flex: 1;
}

.fun-fact-label {
  font-size: 0.7rem;
  font-weight: 900;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  opacity: 0.6;
}

@keyframes bounce-in {
  0%   { opacity: 0; transform: scale(0.3); }
  55%  { opacity: 1; transform: scale(1.08); }
  75%  { transform: scale(0.96); }
  100% { opacity: 1; transform: scale(1); }
}
</style>
