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
layout: default
---

# Australia is Special! 🌏

<div class="grid grid-cols-2 gap-8 mt-3 items-center">
<div class="flex flex-col gap-3">

Australia is both a **continent** and a **country!**

Surrounded by ocean, its animals have been **cut off from the world for millions of years**

That's why it has creatures found **NOWHERE else on Earth!**

🦘 **Marsupials** — carry babies in pouches!

🦔 **Monotremes** — lay eggs but are mammals!

🐊 **Reptiles** — some of the world's most fearsome!

🐦 **Birds** — with very unusual talents!

</div>
<AustraliaMap />
</div>

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
