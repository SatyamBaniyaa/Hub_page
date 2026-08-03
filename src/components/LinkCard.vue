<script setup>
import { ref } from 'vue'

const props = defineProps({
  href: { type: String, required: true },
  title: { type: String, required: true },
  description: { type: String, required: true },
  cta: { type: String, required: true },
  featured: { type: Boolean, default: false },
})

const isHovering = ref(false)
const cardRef = ref(null)

function onMouseMove(e) {
  const card = cardRef.value
  if (!card) return

  const rect = card.getBoundingClientRect()
  const x = e.clientX - rect.left
  const y = e.clientY - rect.top

  const centerX = rect.width / 2
  const centerY = rect.height / 2

  const rotateX = ((y - centerY) / centerY) * -6
  const rotateY = ((x - centerX) / centerX) * 6

  card.style.transform =
    `perspective(800px) rotateX(${rotateX}deg) rotateY(${rotateY}deg) translateY(-2px)`
  card.style.boxShadow =
    props.featured
      ? `0 20px 40px -8px rgba(184,135,74,0.15), 0 8px 16px -6px rgba(184,135,74,0.08)`
      : `0 20px 40px -8px rgba(124,58,237,0.1), 0 8px 16px -6px rgba(124,58,237,0.05)`
}

function onMouseLeave() {
  const card = cardRef.value
  if (!card) return
  card.style.transform = 'perspective(800px) rotateX(0deg) rotateY(0deg) translateY(0)'
  card.style.boxShadow = 'none'
  isHovering.value = false
}
</script>

<template>
  <a :href="href" target="_blank" rel="noopener noreferrer" class="group block no-underline perspective-1000"
    @mouseenter="isHovering = true" @mouseleave="onMouseLeave">
    <div ref="cardRef"
      class="relative flex flex-col justify-between gap-4 rounded-2xl p-6 cursor-pointer transition-all duration-200 ease-out preserve-3d theme-transition"
      :class="[featured ? 'hover:shadow-lg' : 'hover:shadow-lg']" :style="{
        backgroundColor: 'var(--bg-card)',
        border: featured ? '1px solid rgba(184,135,74,0.2)' : '1px solid var(--border-card)',
      }" @mousemove="onMouseMove">
      <!-- Left accent bar for featured -->
      <div v-if="featured"
        class="absolute left-0 top-3 bottom-3 w-[3px] rounded-r-full bg-gradient-to-b from-gold via-gold-soft to-gold-deep">
      </div>

      <div class="flex flex-col gap-3 min-w-0 relative z-10">
        <!-- Icon container with subtle gradient -->
        <div class="w-10 h-10 rounded-xl flex items-center justify-center transition-all duration-300 ease-out" :class="[
          featured
            ? 'bg-gradient-to-br from-gold-50 to-amber-50 group-hover:from-gold-100 group-hover:to-amber-100'
            : 'bg-gradient-to-br from-gray-50 to-gray-100 group-hover:from-violet-50 group-hover:to-violet-100',
          isHovering ? 'scale-105' : ''
        ]">
          <slot name="icon" />
        </div>
        <div class="min-w-0">
          <div class="flex items-center gap-2 mb-1">
            <h2 class="text-base font-semibold theme-transition transition-all duration-300 smooth-weight card-title"
              :class="[featured ? 'featured-title' : '']" :style="{ color: 'var(--text-primary)' }">
              {{ title }}
            </h2>
            <span v-if="featured"
              class="text-[10px] font-semibold uppercase tracking-wider px-2 py-0.5 rounded-full bg-gradient-to-r from-gold-50 to-amber-50 text-gold-deep border border-gold/20 shrink-0">
              Featured
            </span>
          </div>
          <p class="text-sm leading-relaxed transition-colors duration-200 group-hover:opacity-80 theme-transition"
            :style="{ color: 'var(--text-secondary)' }">
            {{ description }}
          </p>
        </div>
      </div>

      <!-- CTA -->
      <span
        class="self-start inline-flex items-center gap-1.5 text-xs font-medium rounded-lg px-4 py-1.5 transition-all duration-200 ease-out"
        :class="[
          featured
            ? 'text-gold-deep bg-gradient-to-r from-gold-50 to-amber-50 hover:from-gold-100 hover:to-amber-100'
            : 'text-violet-700 bg-gradient-to-r from-violet-50 to-violet-50 hover:from-violet-100 hover:to-violet-100',
          isHovering ? 'gap-2' : ''
        ]">
        <span>{{ cta }}</span>
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round"
          stroke-linejoin="round" class="w-3 h-3 transition-transform duration-200 ease-out group-hover:translate-x-1">
          <path d="M5 12h14" />
          <path d="m12 5 7 7-7 7" />
        </svg>
      </span>
    </div>
  </a>
</template>

<style scoped>
.card-title {
  font-variation-settings: 'wght' 600;
  transition: font-variation-settings 0.3s ease, color 0.3s ease, letter-spacing 0.3s ease;
}

.group:hover .card-title:not(.featured-title) {
  color: #7c3aed;
  font-variation-settings: 'wght' 800;
  letter-spacing: 0.02em;
}

.featured-title {
  font-variation-settings: 'wght' 600;
}

.group:hover .featured-title {
  font-variation-settings: 'wght' 800;
  letter-spacing: 0.02em;
}
</style>
