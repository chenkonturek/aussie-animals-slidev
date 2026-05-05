<script setup lang="ts">
import { ref, computed } from 'vue'

interface QuizQuestion {
  question: string
  options: string[]
  correct: number
  explanation: string
}

const props = defineProps<{
  questions: QuizQuestion[]
  quizId?: string
}>()

const currentIndex = ref(0)
const selectedAnswer = ref<number | null>(null)
const isAnswered = ref(false)
const score = ref(0)
const isComplete = ref(false)

const currentQuestion = computed(() => props.questions[currentIndex.value])
const isCorrect = computed(() => selectedAnswer.value === currentQuestion.value.correct)
const progressPct = computed(() =>
  ((currentIndex.value + (isComplete.value ? 1 : 0)) / props.questions.length) * 100
)

function selectAnswer(idx: number) {
  if (isAnswered.value) return
  selectedAnswer.value = idx
  isAnswered.value = true
  if (idx === currentQuestion.value.correct) score.value++
}

function nextQuestion() {
  if (currentIndex.value < props.questions.length - 1) {
    currentIndex.value++
    selectedAnswer.value = null
    isAnswered.value = false
  } else {
    isComplete.value = true
  }
}

function resetQuiz() {
  currentIndex.value = 0
  selectedAnswer.value = null
  isAnswered.value = false
  score.value = 0
  isComplete.value = false
}

const LETTERS = ['A', 'B', 'C', 'D']
</script>

<template>
  <div class="quiz-wrapper">

    <!-- Progress bar -->
    <div class="quiz-progress-track">
      <div class="quiz-progress-bar" :style="{ width: `${progressPct}%` }" />
      <span class="quiz-progress-label">
        {{ isComplete ? 'Finished!' : `Question ${currentIndex + 1} of ${questions.length}` }}
      </span>
    </div>

    <!-- Question view -->
    <Transition name="slide-fade" mode="out-in">

      <div v-if="!isComplete" :key="currentIndex" class="question-panel">

        <h2 class="question-text">{{ currentQuestion.question }}</h2>

        <div class="options-grid">
          <button
            v-for="(option, idx) in currentQuestion.options"
            :key="idx"
            class="option-btn"
            :class="{
              'is-correct':  isAnswered && idx === currentQuestion.correct,
              'is-wrong':    isAnswered && idx === selectedAnswer && !isCorrect,
              'is-selected': idx === selectedAnswer,
            }"
            :disabled="isAnswered"
            @click="selectAnswer(idx)"
          >
            <span class="option-letter">{{ LETTERS[idx] }}</span>
            {{ option }}
          </button>
        </div>

        <!-- Explanation panel -->
        <Transition name="fade">
          <div
            v-if="isAnswered"
            class="explanation-panel"
            :class="isCorrect ? 'correct-panel' : 'wrong-panel'"
          >
            <span class="result-icon">{{ isCorrect ? '🎉' : '😢' }}</span>
            <div class="result-body">
              <p class="result-title">{{ isCorrect ? 'Correct!' : 'Not quite!' }}</p>
              <p class="result-explanation">{{ currentQuestion.explanation }}</p>
            </div>
            <button class="next-btn" @click="nextQuestion">
              {{ currentIndex < questions.length - 1 ? 'Next →' : 'See Score! 🌟' }}
            </button>
          </div>
        </Transition>

      </div>

      <!-- Score summary -->
      <div v-else key="complete" class="score-panel">
        <div class="score-trophy">
          {{ score === questions.length ? '🏆' : score >= Math.ceil(questions.length / 2) ? '🌟' : '💪' }}
        </div>
        <h2 class="score-title">
          {{ score }} / {{ questions.length }} correct!
        </h2>
        <p class="score-message">
          {{
            score === questions.length
              ? "Perfect! You're an Australian animal genius!"
              : score >= Math.ceil(questions.length / 2)
                ? "Great job! You know so much about Australian animals!"
                : "Keep learning — Australian animals are amazing!"
          }}
        </p>
        <button class="reset-btn" @click="resetQuiz">Try Again 🔄</button>
      </div>

    </Transition>

  </div>
</template>

<style scoped>
.quiz-wrapper {
  background: #fff;
  border-radius: 28px;
  padding: 1.75rem 2rem;
  max-width: 700px;
  width: 100%;
  margin: 0 auto;
  box-shadow: 0 10px 40px rgba(0, 0, 0, 0.12);
}

/* Progress */
.quiz-progress-track {
  background: #f0ebe5;
  border-radius: 99px;
  height: 12px;
  margin-bottom: 1.5rem;
  position: relative;
  overflow: hidden;
}

.quiz-progress-bar {
  height: 100%;
  background: linear-gradient(90deg, #FF6B6B, #FFD93D);
  border-radius: 99px;
  transition: width 0.4s ease;
}

.quiz-progress-label {
  position: absolute;
  inset: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 0.65rem;
  font-weight: 900;
  color: #402312;
  text-transform: uppercase;
  letter-spacing: 0.06em;
}

/* Question */
.question-text {
  font-size: 1.35rem;
  font-weight: 900;
  text-align: center;
  color: #402312;
  margin: 0 0 1.25rem;
  line-height: 1.35;
}

.options-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 0.65rem;
}

.option-btn {
  background: #f8f4f0;
  border: 3px solid transparent;
  border-radius: 14px;
  padding: 0.7rem 0.9rem;
  font-size: 0.95rem;
  font-weight: 700;
  font-family: inherit;
  cursor: pointer;
  text-align: left;
  display: flex;
  align-items: center;
  gap: 0.6rem;
  color: #333;
  transition: background 0.15s, border-color 0.15s, transform 0.12s;
  line-height: 1.3;
}

.option-btn:hover:not(:disabled) {
  background: #fff0e6;
  border-color: #FF6B6B;
  transform: translateY(-2px);
}

.option-btn:disabled { cursor: default; }
.option-btn.is-correct { background: #d4f5e2; border-color: #34a853; }
.option-btn.is-wrong   { background: #ffd7d7; border-color: #e53935; }

.option-letter {
  background: #402312;
  color: #fff;
  border-radius: 50%;
  min-width: 28px;
  height: 28px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 0.75rem;
  font-weight: 900;
  flex-shrink: 0;
}

/* Explanation */
.explanation-panel {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  border-radius: 16px;
  padding: 0.85rem 1rem;
  margin-top: 1rem;
}

.correct-panel { background: #d4f5e2; }
.wrong-panel   { background: #ffd7d7; }

.result-icon { font-size: 2rem; flex-shrink: 0; }

.result-body { flex: 1; }
.result-title {
  font-size: 0.9rem;
  font-weight: 900;
  margin: 0 0 2px;
  color: #333;
}
.result-explanation {
  font-size: 0.82rem;
  font-weight: 600;
  margin: 0;
  color: #444;
  line-height: 1.4;
}

.next-btn,
.reset-btn {
  background: #402312;
  color: #fff;
  border: none;
  border-radius: 30px;
  padding: 0.55rem 1.1rem;
  font-size: 0.85rem;
  font-weight: 900;
  font-family: inherit;
  cursor: pointer;
  white-space: nowrap;
  flex-shrink: 0;
  transition: transform 0.12s, box-shadow 0.12s;
}

.next-btn:hover,
.reset-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
}

/* Score screen */
.score-panel {
  text-align: center;
  padding: 1.5rem 1rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.75rem;
}

.score-trophy { font-size: 4rem; line-height: 1; }

.score-title {
  font-size: 2rem;
  font-weight: 900;
  color: #402312;
  margin: 0;
}

.score-message {
  font-size: 1.1rem;
  font-weight: 700;
  color: #555;
  margin: 0;
  max-width: 400px;
  line-height: 1.45;
}

/* Transitions */
.slide-fade-enter-active,
.slide-fade-leave-active {
  transition: all 0.28s ease;
}
.slide-fade-enter-from { opacity: 0; transform: translateX(28px); }
.slide-fade-leave-to   { opacity: 0; transform: translateX(-28px); }

.fade-enter-active,
.fade-leave-active { transition: opacity 0.2s ease; }
.fade-enter-from,
.fade-leave-to     { opacity: 0; }
</style>
