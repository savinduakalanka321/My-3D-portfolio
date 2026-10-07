# Savindu Damsith Akalanka — 3D Portfolio

A full-stack Next.js (App Router) portfolio with a scroll-driven WebGL background, two interactive
React Three Fiber canvases, glassmorphic UI and animated sections.

**Stack:** Next.js 15 · React 19 · TypeScript · Tailwind CSS v4 · Three.js · @react-three/fiber ·
@react-three/drei · Framer Motion

## Run

```bash
npm install
npm run dev      # http://localhost:3000
npm run build    # production build (static prerender)
npm start        # serve the production build
```

## Structure

```
app/
  layout.tsx          SEO metadata, fonts (Sora / Space Grotesk / JetBrains Mono)
  page.tsx            composes the sections
  globals.css         Tailwind v4 theme tokens + glass surfaces
  icon.svg            favicon
components/
  Background3D.tsx    fixed full-page R3F scene: lights, sparkles, drifting solids,
                      profile portrait plane, scroll-driven camera waypoints + pointer parallax
  Navbar.tsx          fixed glass nav with mobile sheet
  Hero3D.tsx          name / role / summary, CTAs, stats, floating profile card
  SkillsCanvas.tsx    3D skill-chip cluster with category filters and hover/click states
  ProjectsSection.tsx 4 orbiting project nodes + detail panel + glass card grid
  TeamworkSection.tsx two teamwork highlight cards + interactive 3D soft-skill network
                      (hover to preview, click / hover the hub for the glass modal)
  ExperienceTimeline.tsx  work, education and certifications
  ContactForm.tsx     validated contact form (opens a pre-filled mail draft)
  Footer.tsx
lib/
  data.ts             all CV content — edit this to update the site
public/
  profile.jpg         portrait placeholder (drop a real photo here)
```

## Notes

- **Content:** every name, skill, project, date and link lives in `lib/data.ts`.
- **Assets:** `public/profile.jpg` is a placeholder portrait; replace it with a real photo
  (square-ish crop works best — the WebGL plane keeps the image's aspect ratio).
- **Performance:** DPR is capped at 1.75, per-frame allocations are avoided, and React Three
  Fiber disposes geometries/materials on unmount. Three canvases are used (background, skills,
  projects) — each only renders while mounted.
- **Accessibility / SEO:** single `<h1>`, semantic sections with headings, labelled nav and form
  fields, `prefers-reduced-motion` disables smooth scrolling, and Next.js metadata/Open Graph are
  configured in `app/layout.tsx`.
