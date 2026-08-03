<script setup>
import { ref } from 'vue'

const socials = [
  {
    name: 'GitHub',
    href: 'https://github.com/yoursfriendlabs',
    path: 'M12 .5C5.73.5.5 5.73.5 12c0 5.08 3.29 9.39 7.86 10.91.57.1.78-.25.78-.55v-2.15c-3.2.7-3.88-1.36-3.88-1.36-.52-1.34-1.28-1.7-1.28-1.7-1.04-.72.08-.7.08-.7 1.15.08 1.76 1.18 1.76 1.18 1.03 1.76 2.7 1.25 3.36.96.1-.75.4-1.25.73-1.53-2.55-.29-5.24-1.28-5.24-5.7 0-1.26.45-2.29 1.18-3.1-.12-.29-.51-1.46.11-3.05 0 0 .97-.31 3.18 1.18a11 11 0 0 1 5.79 0c2.2-1.49 3.17-1.18 3.17-1.18.63 1.59.24 2.76.12 3.05.74.81 1.18 1.84 1.18 3.1 0 4.43-2.7 5.4-5.27 5.69.42.36.78 1.07.78 2.17v3.21c0 .3.2.66.79.55A10.51 10.51 0 0 0 23.5 12C23.5 5.73 18.27.5 12 .5z',
    glow: 'hover:shadow-[0_0_20px_rgba(0,0,0,0.15)] hover:border-gray-500 hover:text-gray-900 hover:bg-gray-50',
  },

  {
    name: 'Facebook',
    href: 'https://www.facebook.com/profile.php?id=61574579494003',
    path: 'M22 12.06C22 6.5 17.52 2 12 2S2 6.5 2 12.06c0 5 3.66 9.15 8.44 9.94v-7.03H7.9v-2.91h2.54V9.85c0-2.5 1.49-3.89 3.77-3.89 1.09 0 2.24.2 2.24.2v2.46h-1.26c-1.24 0-1.63.77-1.63 1.56v1.88h2.78l-.44 2.91h-2.34V22c4.78-.79 8.44-4.94 8.44-9.94z',
    glow: 'hover:shadow-[0_0_20px_rgba(59,89,152,0.35)] hover:border-blue-600 hover:text-blue-700 hover:bg-blue-50',
  },
  {
    name: 'Instagram',
    href: 'https://www.instagram.com/rodilabs/',
    path: 'M12 2.16c3.2 0 3.58.01 4.85.07 1.17.05 1.8.25 2.23.41.56.22.96.48 1.38.9.42.42.68.82.9 1.38.16.42.36 1.06.41 2.23.06 1.27.07 1.65.07 4.85s-.01 3.58-.07 4.85c-.05 1.17-.25 1.8-.41 2.23-.22.56-.48.96-.9 1.38-.42.42-.82.68-1.38.9-.42.16-1.06.36-2.23.41-1.27.06-1.64.07-4.85.07s-3.58-.01-4.85-.07c-1.17-.05-1.8-.25-2.23-.41-.56-.22-.96-.48-1.38-.9-.42-.42-.68-.82-.9-1.38-.16-.42-.36-1.06-.41-2.23-.06-1.27-.07-1.65-.07-4.85s.01-3.58.07-4.85c.05-1.17.25-1.8.41-2.23.22-.56.48-.96.9-1.38.42-.42.82-.68 1.38-.9.42-.16 1.06-.36 2.23-.41 1.27-.06 1.65-.07 4.85-.07zM12 0C8.74 0 8.33.01 7.05.07 5.78.13 4.9.33 4.14.63c-.79.31-1.46.72-2.13 1.38C1.35 2.68.94 3.35.63 4.14.33 4.9.13 5.78.07 7.05.01 8.33 0 8.74 0 12s.01 3.67.07 4.95c.06 1.27.26 2.15.56 2.91.31.79.72 1.46 1.38 2.12.66.66 1.33 1.07 2.12 1.38.76.3 1.64.5 2.91.56C8.33 23.99 8.74 24 12 24s3.67-.01 4.95-.07c1.27-.06 2.15-.26 2.91-.56.79-.31 1.46-.72 2.12-1.38.66-.66 1.07-1.33 1.38-2.12.3-.76.5-1.64.56-2.91.06-1.28.07-1.69.07-4.95s-.01-3.67-.07-4.95c-.06-1.27-.26-2.15-.56-2.91a5.9 5.9 0 0 0-1.38-2.12A5.88 5.88 0 0 0 19.86.63c-.76-.3-1.64-.5-2.91-.56C15.67.01 15.26 0 12 0zm0 5.84A6.16 6.16 0 1 0 18.16 12 6.16 6.16 0 0 0 12 5.84zM12 16a4 4 0 1 1 4-4 4 4 0 0 1-4 4zm6.41-10.85a1.44 1.44 0 1 0 1.44 1.44 1.44 1.44 0 0 0-1.44-1.44z',
    glow: 'hover:shadow-[0_0_20px_rgba(225,48,108,0.35)] hover:border-pink-500 hover:text-pink-600 hover:bg-pink-50',
  },
  {
    name: 'LinkedIn',
    href: 'https://www.linkedin.com/company/rodilabs/posts/?feedView=all',
    path: 'M20.45 20.45h-3.56v-5.57c0-1.33-.02-3.03-1.85-3.03-1.86 0-2.14 1.45-2.14 2.94v5.66H9.34V9h3.42v1.56h.05c.48-.9 1.64-1.85 3.38-1.85 3.6 0 4.27 2.37 4.27 5.46v6.28zM5.34 7.43a2.07 2.07 0 1 1 0-4.13 2.07 2.07 0 0 1 0 4.13zM7.11 20.45H3.56V9h3.55v11.45zM22.22 0H1.77C.8 0 0 .78 0 1.75v20.5C0 23.22.8 24 1.77 24h20.45c.98 0 1.78-.78 1.78-1.75V1.75C24 .78 23.2 0 22.22 0z',
    glow: 'hover:shadow-[0_0_20px_rgba(10,102,194,0.35)] hover:border-blue-600 hover:text-blue-700 hover:bg-blue-50',
  },
  // {
  //   name: 'X (Twitter)',
  //   href: 'https://x.com/',
  //   path: 'M18.24 2h3.5l-7.64 8.73L23 22h-6.98l-5.46-7.14L4.3 22H.8l8.17-9.34L1 2h7.16l4.93 6.52L18.24 2zm-1.23 18h1.94L7.06 3.9H5l11.99 16.1z',
  //   glow: 'hover:shadow-[0_0_15px_rgba(0,0,0,0.1)] hover:border-gray-300 hover:text-gray-800',
  // },
]

const hoveredIcon = ref(null)
const tooltipDir = ref('top')
const iconRefs = ref([])

function onIconEnter(name, index, event) {
  hoveredIcon.value = name
  // Determine tooltip direction based on viewport position
  const rect = event.currentTarget.getBoundingClientRect()
  const spaceAbove = rect.top
  const spaceBelow = window.innerHeight - rect.bottom
  tooltipDir.value = spaceAbove < 80 && spaceBelow > 80 ? 'bottom' : 'top'
}

function onIconMouseMove(e) {
  const link = e.currentTarget
  const rect = link.getBoundingClientRect()
  const x = e.clientX - rect.left - rect.width / 2
  const y = e.clientY - rect.top - rect.height / 2
  const dist = Math.sqrt(x * x + y * y)
  const maxDist = 24
  if (dist < maxDist) {
    const pull = (1 - dist / maxDist) * 0.6
    link.style.transform = `translate(${x * pull}px, ${y * pull}px) scale(1.1)`
  }
}

function onIconMouseLeave(e) {
  const link = e.currentTarget
  link.style.transform = ''
}
</script>

<template>
  <nav class="flex flex-row gap-3" aria-label="Social media links">
    <div v-for="(social, index) in socials" :key="social.name" class="relative"
      @mouseenter="onIconEnter(social.name, index, $event)" @mouseleave="hoveredIcon = null">
      <a :href="social.href" target="_blank" rel="noopener noreferrer" :aria-label="social.name"
        class="w-[52px] h-[52px] rounded-full flex items-center justify-center border-2 transition-all duration-300 hover:scale-110 hover:-translate-y-1 focus-visible:outline-2 focus-visible:outline-violet-500 focus-visible:outline-offset-2 theme-transition social-icon-link"
        :class="social.glow" :style="{
          backgroundColor: 'var(--bg-card)',
          borderColor: 'var(--border-card)',
          color: 'var(--text-secondary)',
        }" @mousemove="onIconMouseMove" @mouseleave="onIconMouseLeave">
        <svg viewBox="0 0 24 24" fill="currentColor" class="w-[20px] h-[20px] transition-transform duration-300">
          <path :d="social.path" />
        </svg>
      </a>
      <!-- Tooltip -->
      <Transition name="tooltip">
        <div v-if="hoveredIcon === social.name" :key="social.name" :class="[
          'absolute left-1/2 -translate-x-1/2 whitespace-nowrap px-3 py-1.5 rounded-lg text-xs font-semibold text-white bg-gray-900/90 border border-gray-700/50 shadow-lg backdrop-blur-sm pointer-events-none z-50',
          tooltipDir === 'top' ? '-top-9' : '-bottom-9'
        ]">
          {{ social.name }}
        </div>
      </Transition>
    </div>
  </nav>
</template>

<style scoped>
.tooltip-enter-active {
  animation: tooltipIn 0.2s ease-out;
}

.tooltip-leave-active {
  animation: tooltipIn 0.15s ease-in reverse;
}

@keyframes tooltipIn {
  0% {
    opacity: 0;
    transform: translateX(-50%) translateY(4px) scale(0.95);
  }

  100% {
    opacity: 1;
    transform: translateX(-50%) translateY(0) scale(1);
  }
}
</style>
