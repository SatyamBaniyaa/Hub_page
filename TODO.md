# Font Life Enhancement Plan

## Step 1: Update `index.html` ✅

- [x] Load Inter as variable font (100–900) with `font-display: swap`
- [x] Load Fraunces as variable font with axes (`wght`, `SOFT`, `WONK`, `opsz`) with `font-display: swap`
- [x] Add preconnect/preload for font performance

## Step 2: Update `src/assets/global.css` ✅

- [x] Add CSS `@font-face` rules with `font-display: swap`
- [x] Add `--font-sans` and `--font-serif` CSS variables
- [x] Add text animation keyframes: `weightPulse`, `weightPulseInter`, `textShimmer`, `letterSpacingBreathe`, `textGlowPulse`
- [x] Add utility classes: `.font-serif-variable`, `.animate-weight-pulse`, `.animate-weight-pulse-inter`, `.animate-text-shimmer`, `.animate-letter-spacing`, `.hover-expand-spacing`, `.text-gradient-live`, `.animate-text-glow`, `.smooth-weight`

## Step 3: Update `src/components/HeroHeader.vue` ✅

- [x] Apply Fraunces variable font with SOFT/WONK axes to "Build • Learn • Grow" tagline using `.font-serif-variable` + `.animate-weight-pulse`
- [x] Add gradient bar shimmer animation
- [x] Add `.hover-expand-spacing` to description text

## Step 4: Update `src/components/LinkCard.vue` ✅

- [x] Add weight animation on hover for card titles using `font-variation-settings`
- [x] Add letter-spacing expansion on hover via scoped CSS

## Step 5: Update `src/components/AppFooter.vue` ✅

- [x] Add continuous gradient animation to "ROdiLabs" using `.text-gradient-live`
- [x] Add `.hover-expand-spacing` on hover
- [x] Add `.smooth-weight` for smooth weight transition
