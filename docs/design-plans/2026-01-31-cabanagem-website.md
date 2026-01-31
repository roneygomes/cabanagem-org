# Cabanagem.org — Website Design

## Summary

This design describes a narrative-driven, single-page website that tells the story of the Cabanagem revolt (1835-1840) to a Brazilian Portuguese-speaking audience, particularly residents of Pará state. The site is structured as a scrolling journey through six main sections: historical context, the revolt itself, key figures, an interactive map, modern legacy, and sources.

The implementation uses Next.js 16 with the App Router, with content authored in MDX files that embed React components for interactivity. The two primary interactive features are a scroll-driven vertical timeline (using Framer Motion animations) and a zoomable Leaflet map showing key locations across Pará. All historical claims will carry inline citations with hover tooltips, feeding into a dedicated bibliography page. The project is structured across eight phases—from scaffolding through deployment on Vercel—building incrementally from infrastructure to content systems to interactive components.

## Definition of Done

**Deliverable:** A comprehensive, single-page or multi-section React website (deployed on Vercel) telling the complete story of the Cabanagem revolt in Pt-BR, targeting the local Paraense population.

**Success criteria:**
- **Content:** Covers precursors (1820s colonial context) → revolt (1835-1840) → modern legacy (place names, cultural memory, annual commemorations)
- **Interactivity:** Scroll-driven animations, interactive timeline, zoomable map of Pará showing key locations/battles
- **Visual:** Space for illustrations and photography throughout; modern, snappy feel inspired by narrative-driven sites like Oxford's AI History
- **Accuracy:** All historical claims sourced; dedicated "Fontes" section with proper citations
- **Characters:** Profiles of key figures (Malcher, Vinagre brothers, Angelim, etc.)
- **Language:** 100% Portuguese (Brasil)

**Out of scope (for now):**
- Actual illustration/photo assets (placeholders in design)
- CMS or admin interface
- Multi-language support

## Glossary

- **Cabanagem**: A popular revolt in the Brazilian province of Grão-Pará (1835-1840), involving indigenous peoples, mestizos, and enslaved Africans against the provincial government. The name derives from "cabanas" (huts) where many rebels lived.
- **Pt-BR**: Portuguese as written and spoken in Brazil, as opposed to European Portuguese.
- **Next.js 16 (App Router)**: A React meta-framework; the App Router is its newer routing architecture using React Server Components and file-based routing under `/app`.
- **MDX**: Markdown extended with JSX, allowing React components to be embedded directly in content files.
- **Framer Motion**: A React animation library providing declarative APIs like `whileInView` for scroll-triggered effects.
- **Leaflet / React Leaflet**: An open-source JavaScript library for interactive maps; React Leaflet provides React bindings for it.
- **Tailwind CSS v4**: A utility-first CSS framework; v4 introduces a new engine and configuration approach.
- **Vercel**: A cloud platform optimized for deploying Next.js applications, with a free tier suitable for static/SSR sites.
- **Frontmatter**: YAML metadata at the top of Markdown/MDX files, used here to store source arrays and event dates.
- **Hash anchors**: URL fragments (e.g., `/#contexto`) that link to specific sections within a single page.
- **`whileInView`**: A Framer Motion prop that triggers animations when an element enters the viewport.
- **Bottom sheet**: A mobile UI pattern where detail content slides up from the bottom of the screen.
- **Parallax**: A visual effect where background elements scroll slower than foreground content, creating depth.
- **`prefers-reduced-motion`**: A CSS media query / browser setting indicating the user prefers minimal animation.
- **OpenGraph metadata**: HTML meta tags that control how a page appears when shared on social platforms.
- **Lighthouse score**: A Google-provided metric (0-100) measuring web page performance, accessibility, and SEO.
- **FCP (First Contentful Paint)**: A Core Web Vital measuring time until the first content appears on screen.
- **WCAG AA**: Web Content Accessibility Guidelines level AA—the standard compliance level for color contrast and accessibility.
- **Lora / Inter**: Typefaces from Google Fonts; Lora is a serif for headlines, Inter a sans-serif for body text.

## Architecture

Single-page scrolling narrative website built with Next.js 16 (App Router), deployed on Vercel. Content authored in MDX with embedded React components for interactivity.

**Core approach:** Scroll-driven storytelling inspired by Oxford's AI History timeline. Users scroll through the complete Cabanagem narrative from colonial precursors (1820s) through the revolt (1835-1840) to modern legacy.

### Site Structure

```
┌─────────────────────────────────────────┐
│  Header (sticky, minimal)               │
│  - Logo: "Cabanagem"                    │
│  - Nav: Contexto | Revolta | Legado | Fontes
│  - Scroll progress indicator            │
└─────────────────────────────────────────┘
│  Hero Section (full viewport)           │
│  Section 1: Contexto (1820s precursors) │
│  Section 2: A Revolta (1835-1840)       │
│    └── Interactive Timeline             │
│  Section 3: Personagens (key figures)   │
│  Section 4: O Mapa da Revolta           │
│    └── Interactive Map of Pará          │
│  Section 5: Legado Hoje                 │
│  Section 6: Fontes e Referências        │
└─────────────────────────────────────────┘
│  Footer                                 │
└─────────────────────────────────────────┘
```

**URL structure:** Single page with hash anchors (`/`, `/#contexto`, `/#revolta`, etc.) for shareability and direct linking.

### Tech Stack

| Layer | Choice |
|-------|--------|
| Framework | Next.js 16 (App Router) |
| Styling | Tailwind CSS v4 |
| Animations | Framer Motion |
| Map | Leaflet + React Leaflet |
| Content | MDX via `@next/mdx` |
| Fonts | Google Fonts (Lora + Inter) |
| Deployment | Vercel (free tier) |
| Language | TypeScript |

### Interactive Components

**Timeline:**
- Vertical, scroll-driven orientation
- Central spine with alternating event cards
- Events reveal via Framer Motion `whileInView`
- Click/tap expands to full detail with citations
- Scope: ~1820 → 1840 → present day legacy markers

**Map:**
- Leaflet with historical-toned base styling
- 8-12 markers for key locations (Belém, Cametá, Santarém, Vigia, battle sites)
- Click markers for event details in sidebar/modal
- Mobile: bottom sheet for location details

### Visual Design

**Color palette:**
- Primary: Deep forest green (`#1a3a2f`)
- Secondary: Earthy terracotta (`#a85a3a`)
- Background: Warm off-white (`#f8f5f0`)
- Text: Near-black (`#1c1c1c`)
- Muted: Parchment tan (`#e8dfd0`)

**Typography:**
- Headlines: Lora (serif, historical gravitas)
- Body: Inter (clean sans-serif, readability)

**Animation system:**
- Scroll into view: Fade-up reveal
- Section entry: Parallax background layers
- Timeline: Cards slide in, spine draws
- Character cards: Subtle hover lift
- Respects `prefers-reduced-motion`

### Content & Sourcing

**AI-assisted workflow:**
1. AI drafts content with inline citation markers
2. Human verification for accuracy and local context
3. Every factual claim linked to source

**Citation system:**
- Inline superscript numbers
- Hover/tap tooltips for source preview
- Dedicated Fontes section with full bibliography

**Content structure:**
```
/content
  /timeline/*.mdx      — event files with sources
  /personagens/*.mdx   — character biographies
  /sections/*.mdx      — narrative content
```

## Existing Patterns

Fresh project — no existing codebase patterns to follow.

This design establishes patterns for:
- MDX content organization with frontmatter source arrays
- Component structure following Next.js App Router conventions
- Animation variants centralized in `/lib/animations.ts`

## Implementation Phases

<!-- START_PHASE_1 -->
### Phase 1: Project Scaffolding

**Goal:** Initialize Next.js project with core dependencies and configuration

**Components:**
- Next.js 16 project via `create-next-app` with App Router
- Tailwind CSS v4 configuration
- TypeScript strict mode
- Framer Motion installation
- Google Fonts (Lora + Inter) setup in layout
- Basic folder structure (`/app`, `/components`, `/content`, `/lib`, `/public`)

**Dependencies:** None (first phase)

**Done when:** `npm run dev` starts successfully, fonts render, Tailwind classes work
<!-- END_PHASE_1 -->

<!-- START_PHASE_2 -->
### Phase 2: Layout & Navigation

**Goal:** Sticky header with navigation and scroll progress indicator

**Components:**
- `app/layout.tsx` — root layout with fonts, metadata
- `app/page.tsx` — main page shell with section anchors
- `components/layout/Header.tsx` — sticky header with nav links
- `components/layout/ScrollProgress.tsx` — progress bar tied to scroll position
- `components/layout/Footer.tsx` — simple footer

**Dependencies:** Phase 1

**Done when:** Header sticks on scroll, nav links scroll to anchors, progress bar updates smoothly
<!-- END_PHASE_2 -->

<!-- START_PHASE_3 -->
### Phase 3: Section Components & Animation System

**Goal:** Reusable section containers with scroll-triggered animations

**Components:**
- `components/ui/Section.tsx` — wrapper with id anchors, padding, background variants
- `components/ui/AnimatedReveal.tsx` — Framer Motion wrapper for fade-up on scroll
- `components/ui/ParallaxBackground.tsx` — parallax effect container
- `lib/animations.ts` — centralized animation variants
- `components/sections/Hero.tsx` — full-viewport hero with title and scroll prompt

**Dependencies:** Phase 2

**Done when:** Hero renders with staggered animation, sections reveal on scroll, parallax works
<!-- END_PHASE_3 -->

<!-- START_PHASE_4 -->
### Phase 4: MDX Content System

**Goal:** MDX pipeline for narrative content with citation support

**Components:**
- `@next/mdx` configuration in `next.config.js`
- `content/sections/contexto.mdx` — sample section content
- `components/content/Citation.tsx` — inline citation with tooltip
- `components/content/SourceTooltip.tsx` — hover preview of source
- `lib/sources.ts` — utility to aggregate sources from MDX frontmatter
- MDX component mapping in `mdx-components.tsx`

**Dependencies:** Phase 3

**Done when:** MDX renders in sections, citations show tooltips, sources extracted from frontmatter
<!-- END_PHASE_4 -->

<!-- START_PHASE_5 -->
### Phase 5: Interactive Timeline

**Goal:** Scroll-driven vertical timeline with expandable events

**Components:**
- `components/timeline/Timeline.tsx` — container with central spine
- `components/timeline/TimelineEvent.tsx` — individual event card with expand/collapse
- `components/timeline/TimelineSpine.tsx` — animated vertical line
- `content/timeline/*.mdx` — 10-15 key event files with dates and sources
- `lib/timeline.ts` — utility to load and sort timeline events

**Dependencies:** Phase 4

**Done when:** Timeline renders events chronologically, cards reveal on scroll, expansion shows full content with sources
<!-- END_PHASE_5 -->

<!-- START_PHASE_6 -->
### Phase 6: Character Profiles

**Goal:** Key figure cards with expandable biographies

**Components:**
- `components/personagens/CharacterGrid.tsx` — responsive grid layout
- `components/personagens/CharacterCard.tsx` — portrait placeholder, name, role, hover effect
- `components/personagens/CharacterModal.tsx` — full biography modal
- `content/personagens/*.mdx` — 5-8 character files (Malcher, Vinagre brothers, Angelim, Batista Campos, etc.)
- `lib/personagens.ts` — utility to load character data

**Dependencies:** Phase 4

**Done when:** Character grid displays, hover effects work, modal shows full biography with sources
<!-- END_PHASE_6 -->

<!-- START_PHASE_7 -->
### Phase 7: Interactive Map

**Goal:** Zoomable map of Pará with location markers

**Components:**
- `components/map/MapContainer.tsx` — Leaflet wrapper with custom styling
- `components/map/LocationMarker.tsx` — custom marker component
- `components/map/LocationDetail.tsx` — sidebar/bottom-sheet for marker details
- `lib/locations.ts` — location data (coordinates, events, descriptions)
- Historical-toned map tile configuration

**Dependencies:** Phase 3

**Done when:** Map renders Pará region, markers show tooltips on hover, click opens detail panel, mobile bottom-sheet works
<!-- END_PHASE_7 -->

<!-- START_PHASE_8 -->
### Phase 8: Fontes Page & Final Polish

**Goal:** Dedicated sources page, SEO, and production readiness

**Components:**
- `app/fontes/page.tsx` — full bibliography page
- `components/fontes/SourceList.tsx` — categorized source display
- OpenGraph metadata and images in `app/layout.tsx`
- `robots.txt` and `sitemap.xml`
- Performance audit and optimization
- Vercel deployment configuration

**Dependencies:** All previous phases

**Done when:** Fontes page lists all sources, Lighthouse score 90+, deployed to Vercel
<!-- END_PHASE_8 -->

## Additional Considerations

**Accessibility:**
- All images have descriptive alt text
- Keyboard navigation for timeline and map
- `prefers-reduced-motion` respected throughout
- Sufficient color contrast (WCAG AA)

**Performance:**
- Next.js Image component with blur placeholders
- Lazy loading for below-fold content
- Target: <150KB JS (gzipped), <1.5s FCP

**Future extensibility:**
- Content structure supports adding more events/characters via MDX
- Map markers defined in data file, easy to expand
- Design accommodates future illustration/photo assets when available
