<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import HeroHeader from './components/HeroHeader.vue'
import LinkCard from './components/LinkCard.vue'
import AppFooter from './components/AppFooter.vue'

const cardsVisible = ref(false)
const mouseX = ref(0)
const mouseY = ref(0)
const orbsRef = ref(null)

onMounted(() => {
  setTimeout(() => {
    cardsVisible.value = true
  }, 300)

  window.addEventListener('mousemove', onMouseMove)
})

onUnmounted(() => {
  window.removeEventListener('mousemove', onMouseMove)
})

function onMouseMove(e) {
  mouseX.value = (e.clientX / window.innerWidth - 0.5) * 2
  mouseY.value = (e.clientY / window.innerHeight - 0.5) * 2

  if (orbsRef.value) {
    const orbs = orbsRef.value.children
    for (let i = 0; i < orbs.length; i++) {
      const depth = 10 + i * 5
      const dx = mouseX.value * depth
      const dy = mouseY.value * depth
      orbs[i].style.transform = `translate(${dx}px, ${dy}px)`
    }
  }
}
</script>

<template>
  <div class="min-h-screen relative overflow-x-hidden theme-transition" style="background-color: var(--bg-primary);">
    <div class="fixed inset-0 -z-10 pointer-events-none bg-noise"></div>
    <div class="fixed inset-0 -z-10 pointer-events-none bg-grid"></div>
    <div ref="orbsRef" class="fixed inset-0 -z-20 pointer-events-none overflow-hidden">
      <div
        class="absolute -top-32 -left-32 h-[30rem] w-[30rem] rounded-full animate-float-slow transition-transform duration-500 ease-out"
        style="background: radial-gradient(circle, var(--orb-violet) 0%, transparent 70%);"></div>
      <div
        class="absolute -top-16 right-[-8rem] h-[24rem] w-[24rem] rounded-full animate-float-slower transition-transform duration-500 ease-out"
        style="background: radial-gradient(circle, var(--orb-gold) 0%, transparent 70%);"></div>
      <div
        class="absolute bottom-[-6rem] -left-16 h-[20rem] w-[20rem] rounded-full animate-float transition-transform duration-500 ease-out"
        style="background: radial-gradient(circle, var(--orb-pink) 0%, transparent 70%);"></div>
      <div
        class="absolute bottom-[-4rem] right-[-4rem] h-[22rem] w-[22rem] rounded-full animate-float-slow transition-transform duration-500 ease-out"
        style="background: radial-gradient(circle, var(--orb-indigo) 0%, transparent 70%);"></div>
      <div
        class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 h-[40rem] w-[40rem] rounded-full animate-glow-pulse transition-transform duration-500 ease-out"
        style="background: radial-gradient(circle, var(--orb-center) 0%, transparent 70%);"></div>
    </div>
    <div class="min-h-screen flex items-center justify-center px-5 py-16 relative">
      <div class="w-full max-w-[1100px] flex flex-col gap-12 lg:gap-16">
        <HeroHeader />
        <Transition name="card-stagger" mode="out-in">
          <main v-if="cardsVisible" key="content" class="flex flex-row flex-wrap justify-center gap-4 lg:gap-5 w-full">
            <div class="animate-fade-in-up w-full sm:w-[calc(33.333%-12px)] min-w-[260px] max-w-sm"
              style="animation-delay: 0.1s; animation-fill-mode: both;">
              <LinkCard href="https://www.yoursfriend.com/#programs" title="Courses"
                description="Industry-focused courses designed to help you build practical skills and advance your career in technology."
                cta="Explore Courses">
                <template #icon>
                  <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6" stroke-linecap="round"
                    stroke-linejoin="round" class="w-5 h-5 text-violet-soft">
                    <path d="M2 5.5 12 2l10 3.5-10 3.5-10-3.5Z" />
                    <path d="M6 8.6v5.6c0 1.4 2.7 2.8 6 2.8s6-1.4 6-2.8V8.6" />
                    <path d="M22 5.5v7" />
                  </svg>
                </template>
              </LinkCard>
            </div>
            <div class="animate-fade-in-up w-full sm:w-[calc(33.333%-12px)] min-w-[260px] max-w-sm"
              style="animation-delay: 0.2s; animation-fill-mode: both;">
              <LinkCard href="https://pasalmanager.com/" title="PasalManager"
                description="An all-in-one POS and inventory platform built to streamline operations and accelerate business growth."
                cta="View Product" featured>
                <template #icon>
                  <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6" stroke-linecap="round"
                    stroke-linejoin="round" class="w-5 h-5 text-gold">
                    <path d="M3 9.5 4.5 4h15L21 9.5" />
                    <path d="M3 9.5h18v9a1 1 0 0 1-1 1H4a1 1 0 0 1-1-1v-9Z" />
                    <path d="M8.5 13.5a2.5 2.5 0 0 0 5 0" />
                  </svg>
                </template>
              </LinkCard>
            </div>
            <div class="animate-fade-in-up w-full sm:w-[calc(33.333%-12px)] min-w-[260px] max-w-sm"
              style="animation-delay: 0.3s; animation-fill-mode: both;">
              <LinkCard href="https://www.yoursfriend.com/" title="Explore More"
                description="Explore our products, open-source projects, resources, and the innovations we are building for the future."
                cta="Discover More">
                <template #icon>
                  <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6" stroke-linecap="round"
                    stroke-linejoin="round" class="w-5 h-5 text-gray-400">
                    <rect x="3" y="3" width="7" height="7" rx="1.5" />
                    <rect x="14" y="3" width="7" height="7" rx="1.5" />
                    <rect x="3" y="14" width="7" height="7" rx="1.5" />
                    <rect x="14" y="14" width="7" height="7" rx="1.5" />
                  </svg>
                </template>
              </LinkCard>
            </div>
          </main>
          <main v-else key="skeleton" class="flex flex-row flex-wrap justify-center gap-4 lg:gap-5 w-full">
            <div v-for="i in 3" :key="i"
              class="theme-transition rounded-2xl p-7 sm:p-8 w-full sm:w-[calc(33.333%-12px)] min-w-[260px] max-w-sm"
              style="background-color: var(--bg-card); border: 1px solid var(--border-card);">
              <div class="flex flex-col gap-4">
                <div class="w-10 h-10 rounded-xl skeleton-pulse"></div>
                <div class="space-y-3">
                  <div class="h-5 w-28 skeleton-pulse rounded-lg"></div>
                  <div class="h-3 w-full skeleton-pulse rounded-lg"></div>
                  <div class="h-3 w-3/4 skeleton-pulse rounded-lg"></div>
                </div>
              </div>
            </div>
          </main>
        </Transition>
        <div class="animate-fade-in-up" style="animation-delay: 0.4s; animation-fill-mode: both;">
          <AppFooter />
        </div>
      </div>
    </div>
  </div>
</template>

<style>
.card-stagger-enter-active {
  transition: all 0.5s ease-out;
}

.card-stagger-enter-from {
  opacity: 0;
  transform: translateY(16px);
}

.card-stagger-leave-active {
  transition: all 0.3s ease-in;
}

.card-stagger-leave-to {
  opacity: 0;
  transform: translateY(-8px);
}
</style>
