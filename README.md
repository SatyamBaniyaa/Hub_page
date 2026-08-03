# YoursFriend Labs — Link Hub

A Vue 3 + Vite link-hub / digital business card page. Light theme, minimal, glass cards.

## Setup

```bash
npm install
npm run dev
```

Build for production:

```bash
npm run build
```

## Adding your real logo

I wasn't able to pull an actual logo image out of the GitHub repo you linked
(`SatyamBaniyaa/Landing_page`) — GitHub blocks automated access to its raw
files and file browser, and I couldn't find a deployed copy of the site either.
Until a real logo is added, the header shows a "YF" monogram placeholder
(`src/components/AppLogo.vue`).

To use your real logo:

1. Drop your logo image into `public/logo.png` (square image, any resolution).
2. That's it — `AppLogo.vue` already points at `/logo.png` and will pick it up
   automatically. If the file isn't there, it falls back to the monogram.

## Project structure

```
index.html                 Vite entry HTML (Tailwind loaded via CDN script)
src/
  main.js                  App bootstrap
  App.vue                  Page layout
  components/
    AppLogo.vue             Logo with monogram fallback
    HeroHeader.vue           Logo + name + tagline + description + socials
    SocialIcons.vue          Social icon row (edit the `socials` array for real URLs)
    LinkCard.vue              Reusable card (Courses / PasalManager / More)
    AppFooter.vue             Minimal footer
public/
  favicon.svg
  logo.png                  ← add your real logo here
```

## Things to update before shipping

- Social links in `src/components/SocialIcons.vue` (currently placeholder `#` / root URLs)
- Card links (`href="#"`) in `src/App.vue` for Courses and PasalManager
- `public/logo.png` — your real logo
"# Hub_page" 
"# Hub_page" 
