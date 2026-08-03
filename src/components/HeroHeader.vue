<script setup>
import SocialIcons from './SocialIcons.vue'
</script>

<template>
  <header class="flex flex-col lg:flex-row lg:items-start justify-between gap-10 lg:gap-16 animate-fade-in-down">
    <div class="flex flex-col gap-5 max-w-lg">
      <!-- Brand with decorative glow dot -->
      <div class="flex items-center gap-3 group">
        <div class="relative w-52 h-12 flex-shrink-0">
          <div
            class="absolute -inset-4 rounded-full opacity-0 group-hover:opacity-100 transition-opacity duration-500 pointer-events-none"
            style="background: radial-gradient(circle, rgba(124,58,237,0.08) 0%, transparent 70%);">
          </div>
          <img src="/logo.svg" alt="RodiLabs logo" class="w-full h-full object-contain relative z-10" />
        </div>
      </div>

      <div class="relative">
        <div
          class="w-14 h-[3px] rounded-full bg-gradient-to-r from-violet-400 via-gold to-transparent mb-4 animate-gradient-bar">
        </div>
        <p class="font-serif-variable font-medium text-xs uppercase tracking-[0.25em] theme-transition animate-weight-pulse"
          style="color: var(--text-primary); opacity: 0.85;">
          Build <span class="theme-transition" style="color: var(--text-muted); opacity: 0.7;">•</span> Learn <span
            class="theme-transition" style="color: var(--text-muted); opacity: 0.7;">•</span> Grow
        </p>
      </div>

      <p class="text-lg sm:text-xl leading-relaxed font-medium theme-transition hover-expand-spacing"
        style="color: var(--text-secondary);">
        Building innovative software products, premium learning experiences, and modern digital
        solutions for businesses and developers.
      </p>
    </div>

    <SocialIcons class="flex-shrink-0 self-start lg:self-auto" />
  </header>
</template>

<style scoped>
@keyframes gradientBarShimmer {
  0% {
    opacity: 0.6;
    transform: scaleX(1);
  }

  50% {
    opacity: 1;
    transform: scaleX(1.1);
  }

  100% {
    opacity: 0.6;
    transform: scaleX(1);
  }
}

.animate-gradient-bar {
  animation: gradientBarShimmer 3s ease-in-out infinite;
  transform-origin: left center;
}
</style>
