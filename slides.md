---
theme: shibainu
title: "Amazing Australian Animals! 🦘"
fonts:
  sans: Nunito
  weights: "400,700,900"
  provider: google
transition: slide-left
aspectRatio: "16/9"
---

# Amazing Australian Animals! 🦘

**Discover the weird and wonderful creatures of Australia**

<div class="text-center mt-6 text-6xl tracking-widest">🦘 🐨 🦔 🐾 🦫 🐦</div>

---
layout: none
---

<div class="spl-slide">

  <div class="spl-left">
    <h1 class="spl-title">Australia is Special! 🌏</h1>
    <p class="spl-intro">
      The world's only country that's also a <strong>continent</strong>.
      Millions of years of ocean isolation created animals found
      <strong>nowhere else on Earth.</strong>
    </p>
    <div class="spl-chips">
      <div class="spl-chip" style="background:#FF8FA3">
        <span class="spl-chip-emoji">🦘</span>
        <div><strong>Marsupials</strong><small>Babies in pouches</small></div>
      </div>
      <div class="spl-chip" style="background:#FFD93D">
        <span class="spl-chip-emoji">🦔</span>
        <div><strong>Monotremes</strong><small>Egg-laying mammals</small></div>
      </div>
      <div class="spl-chip" style="background:#95E1D3">
        <span class="spl-chip-emoji">🐊</span>
        <div><strong>Reptiles</strong><small>World's most fearsome</small></div>
      </div>
      <div class="spl-chip" style="background:#B8F5C8">
        <span class="spl-chip-emoji">🐦</span>
        <div><strong>Unique Birds</strong><small>Extraordinary talents</small></div>
      </div>
    </div>
  </div>

  <div class="spl-right">
    <AustraliaMap />
  </div>

</div>

<style>
.spl-slide {
  position: absolute;
  inset: 0;
  display: grid;
  grid-template-columns: 1fr 1fr;
  font-family: 'Nunito', sans-serif;
}
.spl-left {
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding: 3rem 2.5rem 3rem 3.5rem;
  background: linear-gradient(155deg, #fff8f0 0%, #fef0d8 100%);
  gap: 1.4rem;
}
.spl-title {
  font-size: 2.2rem;
  font-weight: 900;
  color: #402312;
  line-height: 1.2;
  margin: 0;
}
.spl-intro {
  font-size: 1rem;
  line-height: 1.7;
  color: #444;
  margin: 0;
}
.spl-intro strong { color: #402312; }
.spl-chips {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 0.75rem;
}
.spl-chip {
  display: flex;
  align-items: center;
  gap: 0.65rem;
  border-radius: 16px;
  padding: 0.75rem 1rem;
  box-shadow: 0 3px 10px rgba(0,0,0,0.08);
}
.spl-chip-emoji { font-size: 1.8rem; flex-shrink: 0; line-height: 1; }
.spl-chip strong { display: block; font-size: 0.88rem; font-weight: 900; color: #222; }
.spl-chip small  { display: block; font-size: 0.72rem; font-weight: 600; opacity: 0.7; margin-top: 1px; }
.spl-right {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 2.5rem;
  background: linear-gradient(155deg, #c5e8f5 0%, #90cbe8 100%);
}
</style>

---
layout: section
---

# Meet Our Animal Friends 🐾

**Click on each animal card to discover a fun fact!**

---
layout: center
---

## Kangaroo & Koala

<AnimalGrid :animals="['kangaroo', 'koala']" :columns="2" />

---
layout: center
---

## Platypus & Wombat

<AnimalGrid :animals="['platypus', 'wombat']" :columns="2" />

---
layout: center
---

## Echidna & Kookaburra

<AnimalGrid :animals="['echidna', 'kookaburra']" :columns="2" />

---
layout: default
---

# Did You Know? 🤩

<div class="grid grid-cols-3 gap-5 mt-5 h-56">
  <FunFact
    emoji="🦘"
    fact="A baby kangaroo is called a JOEY and is only 2 cm long at birth — smaller than a grape!"
    color="#FF8FA3"
  />
  <FunFact
    emoji="🐨"
    fact="Koalas sleep up to 22 hours a day! They need all that rest to digest tough eucalyptus leaves."
    color="#95E1D3"
  />
  <FunFact
    emoji="🦫"
    fact="The platypus has a duck bill, beaver tail, AND lays eggs — but it's still a mammal!"
    color="#FFD93D"
  />
</div>

---
layout: default
---

# More Amazing Facts! 🌟

<div class="grid grid-cols-3 gap-5 mt-5 h-56">
  <FunFact
    emoji="🐾"
    fact="Wombats produce cube-shaped poo — the only animal in the ENTIRE world that does this!"
    color="#A8E6CF"
  />
  <FunFact
    emoji="🦔"
    fact="Echidnas have no teeth! They use a 15 cm sticky tongue to slurp up ants and termites."
    color="#FFB347"
  />
  <FunFact
    emoji="🐦"
    fact="The kookaburra laughs to mark its territory. Its call can be heard over a kilometre away!"
    color="#B8F5C8"
  />
</div>

---
layout: section
---

# What's the Difference? 🤔

**Marsupials vs Monotremes**

---
layout: two-cols
---

## Marsupials 🦘

Animals that carry babies in pouches

| Animal | Cool Fact |
|--------|-----------|
| 🦘 Kangaroo | Can jump 9 metres! |
| 🐨 Koala | Only eats eucalyptus |
| 🐾 Wombat | Backwards pouch! |
| 🐭 Possum | Plays dead when scared |

::right::

## Monotremes 🦔

Egg-laying mammals — incredibly rare!

| Animal | Cool Fact |
|--------|-----------|
| 🦫 Platypus | Duck bill + beaver tail |
| 🦔 Echidna | Covered in spines! |

<br>

> Only **5 species** of monotremes exist on Earth — **4 live in Australia!** 🏆

---
layout: section
transition: fade
---

# Quiz Time! 🎉

**How much did you learn about Australian animals?**

<div class="text-5xl mt-4">🧠 Let's find out! 🌟</div>

---
layout: center
---

<AnimalQuiz :questions="quizSlice1" quiz-id="quiz-a" />

<script setup>
const quizSlice1 = [
  {
    question: "What is a baby kangaroo called?",
    options: ["Cub", "Joey", "Kit", "Pup"],
    correct: 1,
    explanation: "A baby kangaroo is called a JOEY! They're tiny — only about 2 cm long at birth! 🦘",
  },
  {
    question: "How many hours a day does a koala sleep?",
    options: ["8 hours", "12 hours", "18 hours", "22 hours"],
    correct: 3,
    explanation: "Koalas sleep up to 22 hours a day! They need all that rest to digest eucalyptus. 😴",
  },
  {
    question: "Which animal lays eggs AND is a mammal?",
    options: ["Kangaroo", "Wombat", "Platypus", "Kookaburra"],
    correct: 2,
    explanation: "The platypus lays eggs but feeds milk to its babies — it's a true monotreme! 🦫",
  },
]
</script>

---
layout: center
---

<AnimalQuiz :questions="quizSlice2" quiz-id="quiz-b" />

<script setup>
const quizSlice2 = [
  {
    question: "What shape is wombat poo?",
    options: ["Round", "Oval", "Cube", "Tube"],
    correct: 2,
    explanation: "Wombats make cube-shaped poo — totally unique in the animal kingdom! 📦",
  },
  {
    question: "What does a kookaburra sound like?",
    options: ["Hissing", "Laughing", "Crying", "Barking"],
    correct: 1,
    explanation: "Kookaburras make a loud laughing call to mark their territory! 😂",
  },
  {
    question: "Which animal uses electric fields to find food?",
    options: ["Echidna", "Wombat", "Koala", "Platypus"],
    correct: 3,
    explanation: "Platypuses detect electric fields from prey in the water — like a superpower! ⚡",
  },
]
</script>

---
layout: center
---

# You're an Australian Animal Expert! 🌟

**Thank you for learning about these incredible creatures!**

<div class="text-5xl mt-5 tracking-widest">🦘 🐨 🦔 🐾 🦫 🐦</div>

<div class="mt-5 text-xl font-bold opacity-70">Remember: Every animal is special and worth protecting! 💚</div>

---
layout: none
---

<div class="cc-slide">

  <img src="/claude-code-logo.png" class="cc-logo" alt="Claude Code logo" />
  <h1 class="cc-title">Meet Claude Code! 🪄</h1>
  <p class="cc-sub">Type what you want — AI builds it for you!</p>

  <div class="cc-reveal">
    <span class="cc-reveal-emoji">🤫</span>
    <span>This <strong>whole slideshow</strong> was made with Claude Code! 🦘🐨🦔</span>
  </div>

  <div class="cc-chips">
    <div class="cc-chip" style="background:#FFE66D">💬<strong>You talk</strong></div>
    <div class="cc-chip" style="background:#95E1D3">🤖<strong>AI codes</strong></div>
    <div class="cc-chip" style="background:#FF8FA3">🎉<strong>Ta-da!</strong></div>
  </div>

</div>

<style>
.cc-slide {
  position: absolute;
  inset: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 1.4rem;
  padding: 2.5rem 3.5rem;
  background: linear-gradient(145deg, #fff7ed 0%, #fef9e7 55%, #f0fdf4 100%);
  font-family: 'Nunito', sans-serif;
}
.cc-logo {
  width: 88px;
  height: 88px;
  object-fit: contain;
  margin-bottom: 0.1rem;
}
.cc-title {
  font-size: 2.8rem;
  font-weight: 900;
  color: var(--color-dark-bark);
  margin: 0;
}
.cc-sub {
  font-size: 1.2rem;
  color: #555;
  margin: 0;
}
.cc-reveal {
  display: flex;
  align-items: center;
  gap: 0.9rem;
  background: var(--color-wattle-yellow);
  border-radius: 18px;
  padding: 0.85rem 1.6rem;
  box-shadow: 0 4px 14px rgba(0,0,0,0.10);
  font-size: 1rem;
  font-weight: 700;
  color: #402312;
  max-width: 600px;
  width: 100%;
}
.cc-reveal-emoji { font-size: 1.8rem; flex-shrink: 0; }
.cc-chips {
  display: flex;
  gap: 0.9rem;
}
.cc-chip {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  border-radius: 14px;
  padding: 0.7rem 1.2rem;
  font-size: 1rem;
  font-weight: 900;
  box-shadow: 0 3px 10px rgba(0,0,0,0.08);
  color: #222;
}
</style>
