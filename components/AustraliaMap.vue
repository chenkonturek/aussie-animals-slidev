<template>
  <div class="aus-map-wrap">
    <svg viewBox="0 0 520 450" xmlns="http://www.w3.org/2000/svg" aria-label="Map of Australia">

      <!-- Ocean -->
      <rect width="520" height="450" rx="18" fill="#89CFF0"/>

      <!-- Soft wave texture lines -->
      <line x1="0" y1="420" x2="520" y2="420" stroke="white" stroke-width="1.5" opacity="0.25"/>
      <line x1="0" y1="410" x2="520" y2="410" stroke="white" stroke-width="1"   opacity="0.18"/>

      <!-- Drop shadow for continent -->
      <path
        d="M 80,155 C 80,127 90,103 112,83 C 134,63 157,53 180,51
           C 194,50 204,55 206,63 L 222,91
           C 238,111 254,115 266,99 L 270,69
           C 280,51 300,43 318,47 C 332,51 342,61 340,73
           L 334,85 C 328,99 328,113 338,129
           C 354,151 372,168 388,193 C 404,218 416,251 420,281
           C 424,308 418,335 406,353 C 392,371 370,377 348,379
           C 324,381 300,373 278,365 C 258,357 240,351 222,357
           C 204,363 184,375 160,379 C 132,383 106,379 86,365
           C 67,351 60,329 64,303 C 68,277 72,251 70,225
           C 68,199 70,173 74,161 Z"
        fill="rgba(0,0,0,0.12)"
        transform="translate(5,5)"
      />

      <!-- Main continent -->
      <path
        d="M 80,155 C 80,127 90,103 112,83 C 134,63 157,53 180,51
           C 194,50 204,55 206,63 L 222,91
           C 238,111 254,115 266,99 L 270,69
           C 280,51 300,43 318,47 C 332,51 342,61 340,73
           L 334,85 C 328,99 328,113 338,129
           C 354,151 372,168 388,193 C 404,218 416,251 420,281
           C 424,308 418,335 406,353 C 392,371 370,377 348,379
           C 324,381 300,373 278,365 C 258,357 240,351 222,357
           C 204,363 184,375 160,379 C 132,383 106,379 86,365
           C 67,351 60,329 64,303 C 68,277 72,251 70,225
           C 68,199 70,173 74,161 Z"
        fill="#E8B84B"
        stroke="#C4973A"
        stroke-width="2.5"
        stroke-linejoin="round"
      />

      <!-- Tasmania -->
      <path
        d="M 374,402 C 380,394 392,394 399,402 C 406,410 402,422 393,424
           C 384,426 374,418 373,408 Z"
        fill="#E8B84B"
        stroke="#C4973A"
        stroke-width="2"
      />

      <!-- Australia label -->
      <text
        x="248" y="232"
        text-anchor="middle"
        font-family="Nunito, sans-serif"
        font-size="17"
        font-weight="900"
        fill="#7A5C0A"
        letter-spacing="4"
        opacity="0.75"
      >AUSTRALIA</text>

      <!-- Ocean labels -->
      <text x="462" y="255" text-anchor="middle" font-family="Nunito,sans-serif"
            font-size="10" font-weight="700" fill="#1a6b9e" opacity="0.85"
            transform="rotate(-90,462,255)">Pacific Ocean</text>
      <text x="32"  y="255" text-anchor="middle" font-family="Nunito,sans-serif"
            font-size="10" font-weight="700" fill="#1a6b9e" opacity="0.85"
            transform="rotate(-90,32,255)">Indian Ocean</text>
      <text x="248" y="438" text-anchor="middle" font-family="Nunito,sans-serif"
            font-size="10" font-weight="700" fill="#1a6b9e" opacity="0.85">Southern Ocean</text>

      <!-- Animal emoji markers -->
      <text x="196" y="108" font-size="22" text-anchor="middle">🐊</text>  <!-- croc — Darwin/north -->
      <text x="210" y="258" font-size="24" text-anchor="middle">🦘</text>  <!-- kangaroo — outback -->
      <text x="370" y="258" font-size="22" text-anchor="middle">🐨</text>  <!-- koala — east coast -->
      <text x="472" y="190" font-size="20" text-anchor="middle">🦈</text>  <!-- shark — Pacific -->

      <!-- Canberra star -->
      <text x="396" y="313" font-size="14" text-anchor="middle">⭐</text>
      <text x="396" y="326" text-anchor="middle" font-family="Nunito,sans-serif"
            font-size="9" font-weight="700" fill="#7A5C0A">Canberra</text>

    </svg>
  </div>
</template>

<style scoped>
.aus-map-wrap {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
}

.aus-map-wrap svg {
  height: 100%;
  width: auto;
  max-height: 320px;
  filter: drop-shadow(0 6px 16px rgba(0, 0, 0, 0.18));
  border-radius: 18px;
}
</style>
