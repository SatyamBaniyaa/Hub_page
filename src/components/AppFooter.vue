<template>
  <footer class="flex flex-col items-center gap-4 pt-4">
    <!-- Decorative sparkle dots -->
    <div class="flex items-center gap-3 mb-1">
      <span class="w-1 h-1 rounded-full" style="background-color: var(--orb-violet);"></span>
      <span class="w-1 h-1 rounded-full" style="background-color: var(--orb-gold);"></span>
      <span class="w-1 h-1 rounded-full" style="background-color: var(--orb-violet);"></span>
    </div>

    <!-- Gradient divider -->
    <div class="w-32 h-px bg-gradient-to-r from-transparent via-violet/40 to-transparent"></div>

    <div class="flex items-center gap-1.5 text-xs tracking-wide theme-transition" style="color: var(--text-muted);">
      <span>Made</span>
      <span style="color: var(--text-muted); opacity: 0.7;">&bull;</span>
      <span>by</span>
      <span class="font-semibold theme-transition text-gradient-live smooth-weight cursor-default hover-expand-spacing"
        style="font-variation-settings: 'wght' 700;">
        ROdiLabs
      </span>
    </div>
  </footer>
</template>
