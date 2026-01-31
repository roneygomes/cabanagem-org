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

## Tasks

Each task represents a cohesive unit of work for an autonomous agent. Tasks must be completed in order due to dependencies.

---

### Task 1: Project Scaffolding

**Description:** Initialize the Next.js 16 project with all foundational dependencies, configuration, and folder structure. This establishes the development environment for all subsequent tasks.

**Blocked by:** None

**Implementation guidance:**
1. Run `pnpm create next-app@latest . --typescript --tailwind --eslint --app --turbopack --yes` to scaffold Next.js 16 project
2. Install framer-motion with `pnpm add framer-motion`
3. Update `app/layout.tsx` to configure Google Fonts (Lora + Inter) with pt-BR metadata, including OpenGraph settings
4. Replace `app/globals.css` with Tailwind v4 theme variables (--color-primary: #1a3a2f, --color-secondary: #a85a3a, --color-background: #f8f5f0, --color-text: #1c1c1c, --color-muted: #e8dfd0) and font-family settings
5. Update `app/page.tsx` with test content showing the color palette
6. Create folder structure with `.gitkeep` files:
   - `components/layout`, `components/ui`, `components/sections`, `components/timeline`, `components/map`, `components/personagens`, `components/content`
   - `content/timeline`, `content/personagens`, `content/sections`
   - `lib`, `types`

**Validation criteria:**
- [ ] `pnpm run dev` starts without errors
- [ ] `pnpm run build` completes successfully
- [ ] `pnpm list framer-motion` shows framer-motion installed
- [ ] Browser shows test page with Lora (serif) and Inter (sans-serif) fonts rendering correctly
- [ ] Color palette variables are visible in test content (green, terracotta, off-white, near-black, tan)
- [ ] All folder structure directories exist
- [ ] `<html lang="pt-BR">` is set in layout

---

### Task 2: Layout & Navigation

**Description:** Build the persistent layout components: sticky header with navigation, scroll progress indicator, and footer. Establish the single-page structure with hash-anchor sections.

**Blocked by:** Task 1

**Implementation guidance:**
1. Create `components/layout/Header.tsx` with sticky header, logo "Cabanagem", nav links (Contexto, A Revolta, Personagens, Mapa, Legado, Fontes), and smooth scroll behavior using `scrollIntoView`
2. Create `components/layout/ScrollProgress.tsx` using Framer Motion `useScroll` and `useSpring` to show progress bar at top-16 (below header)
3. Create `components/layout/Footer.tsx` with project branding and copyright
4. Create `components/layout/index.ts` barrel export for Header, ScrollProgress, Footer
5. Update `app/layout.tsx` to import and render Header, ScrollProgress, and Footer with main wrapped in pt-16 padding
6. Update `app/page.tsx` with placeholder sections (hero, contexto, revolta, personagens, mapa, legado, fontes) with alternating backgrounds and proper id attributes for navigation

**Validation criteria:**
- [ ] `pnpm run build` completes successfully
- [ ] Header is sticky and remains visible while scrolling
- [ ] Clicking nav links scrolls smoothly to corresponding section
- [ ] URL updates with hash anchors (e.g., `/#contexto`) when navigating
- [ ] Scroll progress bar animates from 0% to 100% as user scrolls page
- [ ] Footer appears at bottom of page
- [ ] All sections have visible alternating backgrounds for distinction

---

### Task 3: Section Components & Animation System

**Description:** Create the reusable animation system and section wrapper components. Build the Hero section with scroll-triggered animations. Establish patterns for `prefers-reduced-motion` compliance.

**Blocked by:** Task 2

**Implementation guidance:**
1. Create `lib/animations.ts` with Framer Motion variants: fadeUpVariants, staggerContainerVariants, scaleInVariants, slideInLeftVariants, slideInRightVariants
2. Create `components/ui/AnimatedReveal.tsx` component wrapping children with motion.div using whileInView="visible" and viewport={{ once: true }}, respecting `useReducedMotion`
3. Create `components/ui/ParallaxBackground.tsx` using Framer Motion useScroll and useTransform for parallax effect, respecting reduced motion
4. Create `components/ui/Section.tsx` wrapper component with id prop, background variants (default/muted/primary), padding, and optional fullHeight prop
5. Create `components/ui/index.ts` barrel export for Section, AnimatedReveal, ParallaxBackground
6. Create `components/sections/Hero.tsx` with staggered animation for title "Cabanagem", subtitle about the revolt, description, and scroll arrow indicator
7. Create `components/sections/index.ts` barrel export
8. Update `app/page.tsx` to use Hero and animated Section components with AnimatedReveal for content

**Validation criteria:**
- [ ] `pnpm run build` completes successfully
- [ ] Hero section displays with staggered fade-in animation on page load
- [ ] Scrolling reveals section content with fade-up animations
- [ ] Parallax background effect visible on sections with ParallaxBackground
- [ ] With `prefers-reduced-motion: reduce` enabled in OS/browser, animations are disabled or simplified
- [ ] Scroll arrow indicator animates (bounces or pulses)
- [ ] Section backgrounds alternate correctly (default, muted, primary variants)

---

### Task 4: MDX Content System

**Description:** Set up the MDX pipeline for content authoring with frontmatter support. Build the citation system with inline tooltips and source registry. Create sample content to validate the system.

**Blocked by:** Task 3

**Implementation guidance:**
1. Install MDX dependencies: `pnpm add @next/mdx @mdx-js/loader @mdx-js/react gray-matter` and `pnpm add -D @types/mdx`
2. Update `next.config.ts` to use createMDX wrapper with pageExtensions including .mdx
3. Create `mdx-components.tsx` in root with custom h1/h2/h3/p/blockquote/ul/ol styling using Lora for headings and Inter for body
4. Create `types/content.ts` with:
   - Source interface (id, author, title, year, publisher?, url?, accessDate?, pages?)
   - ContentFrontmatter, TimelineEventFrontmatter, PersonagemFrontmatter types
5. Create `lib/sources.ts` with sourcesRegistry Map, registerSource, getSource, getAllSources, formatSourceCitation, formatSourceUrl utilities
6. Create `components/content/SourceTooltip.tsx` with positioned tooltip showing formatted citation
7. Create `components/content/Citation.tsx` as inline superscript component with hover/focus tooltip using SourceTooltip
8. Create `lib/content-loader.ts` with loadContentFile and loadAllContent functions using gray-matter, registering sources from frontmatter
9. Create `content/sections/contexto.mdx` with sample content about colonial context, frontmatter sources array, and Citation usage examples
10. Create `components/sections/ContentSection.tsx` wrapping Section and AnimatedReveal with prose styling

**Validation criteria:**
- [ ] `pnpm run build` completes successfully
- [ ] MDX files in content/ are parseable without errors
- [ ] Frontmatter is correctly extracted from MDX files (test with console.log or debug)
- [ ] Citation components render as superscript numbers (e.g., ¹, ², ³)
- [ ] Hovering over a citation shows tooltip with formatted source information
- [ ] Custom MDX typography styles apply (Lora headings, Inter body)
- [ ] ContentSection renders contexto.mdx content with animations

---

### Task 5: Interactive Timeline

**Description:** Build the scroll-driven vertical timeline showing key events from 1835-1840. Create expandable event cards with alternating left/right layout and source citations. Populate with 3+ historical events.

**Blocked by:** Task 4

**Implementation guidance:**
1. Create `lib/timeline.ts` with TimelineEvent interface, loadTimelineEvents function reading from content/timeline/*.mdx, parseDate and formatEventDate utilities for Portuguese date formatting (e.g., "7 de janeiro de 1835")
2. Create `components/timeline/TimelineSpine.tsx` with Framer Motion scroll-linked height animation for the central vertical line
3. Create `components/timeline/TimelineEvent.tsx` with:
   - Expandable card showing date, title, description
   - Full content revealed on expand
   - Sources footer with citations
   - Alternating left/right layout based on index
   - Keyboard accessible (Enter/Space to expand)
4. Create `components/timeline/Timeline.tsx` container with Section wrapper, heading "A Revolta", TimelineSpine, and mapped TimelineEvent components
5. Create `components/timeline/index.ts` barrel export
6. Create timeline event MDX files with frontmatter (title, date, location, description, sources):
   - `content/timeline/1835-01-07-tomada-belem.mdx` - Taking of Belém
   - `content/timeline/1835-02-vinagre.mdx` - Francisco Vinagre assumes power
   - `content/timeline/1836-angelim.mdx` - Eduardo Angelim's leadership
7. Update `app/page.tsx` to import Timeline and loadTimelineEvents, make component async, render Timeline in the revolta section
8. Add responsive mobile styles: all cards on left with left-aligned spine on mobile (< md breakpoint)

**Validation criteria:**
- [ ] `pnpm run build` completes successfully
- [ ] Timeline displays with central vertical spine
- [ ] Spine animates/draws as user scrolls into view
- [ ] Event cards appear alternating left and right on desktop
- [ ] Event cards appear all on left on mobile (< 768px)
- [ ] Clicking/tapping an event card expands to show full content
- [ ] Keyboard navigation works (Tab to focus, Enter/Space to expand)
- [ ] Dates display in Portuguese format (e.g., "7 de janeiro de 1835")
- [ ] At least 3 timeline events render with content and sources

---

### Task 6: Character Profiles

**Description:** Create the character showcase section with card grid and modal biographies. Build profiles for 4 key historical figures with portraits (placeholders), biographies, and source citations.

**Blocked by:** Task 5

**Implementation guidance:**
1. Create `lib/personagens.ts` with Personagem interface, loadPersonagens function reading from content/personagens/*.mdx, formatLifespan utility (e.g., "1790-1835")
2. Create `components/personagens/CharacterCard.tsx` with:
   - Portrait placeholder (colored div or SVG silhouette)
   - Name, role, lifespan
   - Hover lift effect (translateY with shadow)
   - Keyboard accessible (focusable, Enter to open modal)
3. Create `components/personagens/CharacterModal.tsx` with:
   - React portal for proper stacking
   - Framer Motion enter/exit animations
   - Portrait, name, role, full biography
   - Sources footer
   - Close on X button, backdrop click, or Escape key
   - Focus trap (focus stays within modal while open)
4. Create `components/personagens/CharacterGrid.tsx` container with Section wrapper, heading "Personagens", responsive grid (1 col mobile, 2 col tablet, 4 col desktop), state for selected personagem, CharacterCard mapping, CharacterModal
5. Create `components/personagens/index.ts` barrel export
6. Create character MDX files with frontmatter (name, role, birthYear, deathYear, description, sources):
   - `content/personagens/malcher.mdx` - Félix Clemente Malcher
   - `content/personagens/vinagre.mdx` - Francisco Vinagre
   - `content/personagens/angelim.mdx` - Eduardo Angelim
   - `content/personagens/batista-campos.mdx` - Cônego Batista Campos
7. Update `app/page.tsx` to import CharacterGrid and loadPersonagens, render CharacterGrid after Timeline

**Validation criteria:**
- [ ] `pnpm run build` completes successfully
- [ ] Character grid displays 4 character cards in responsive layout
- [ ] Cards show portrait placeholder, name, role, lifespan
- [ ] Hovering card shows lift effect
- [ ] Clicking card opens modal with full biography
- [ ] Modal can be closed via X button, backdrop click, or Escape key
- [ ] Focus is trapped within modal while open
- [ ] Tab navigation works through cards
- [ ] Sources display in modal footer

---

### Task 7: Interactive Map

**Description:** Build the interactive Leaflet map of Pará showing key locations and battle sites. Create location markers with detail panels (sidebar on desktop, bottom sheet on mobile). Handle SSR compatibility.

**Blocked by:** Task 6

**Implementation guidance:**
1. Install Leaflet: `pnpm add leaflet react-leaflet` and `pnpm add -D @types/leaflet`
2. Create `types/map.ts` with MapLocation interface (id, name, coordinates: [lat, lng], type: 'city' | 'battle', description, events: LocationEvent[]) and LocationEvent interface
3. Create `lib/locations.ts` with:
   - locations array: Belém, Cametá, Santarém, Vigia, Acará, Ecuipiranga, Abaetetuba, Breves
   - getLocationById, getLocationsByType utilities
   - PARA_BOUNDS and PARA_CENTER constants for map positioning
4. Create `components/map/LocationMarker.tsx` using react-leaflet Marker with custom icons by type (city=primary green, battle=secondary terracotta), Tooltip on hover, onClick handler
5. Create `components/map/LocationDetail.tsx` with:
   - Responsive layout: sidebar (md:absolute right) on desktop, bottom sheet on mobile
   - Location name, type badge, description, events list
   - Close button
   - Framer Motion slide-in animations
6. Add Leaflet CSS import to `app/globals.css`: `@import "leaflet/dist/leaflet.css";`
7. Create `components/map/MapContainer.tsx` (export as MapSection) with:
   - Section wrapper, heading "O Mapa da Revolta"
   - Legend explaining marker colors
   - LeafletMap using MapContainer and TileLayer (CARTO light tiles: `https://{s}.basemaps.cartocdn.com/light_all/{z}/{x}/{y}{r}.png`)
   - LocationMarker for each location
   - LocationDetail panel (conditionally rendered when location selected)
   - Loading placeholder while map initializes
   - `isMounted` state check for SSR safety
   - Use Next.js dynamic import with `{ ssr: false }` for react-leaflet components
8. Create `components/map/index.ts` barrel export
9. Update `app/page.tsx` to import MapSection and render after CharacterGrid

**Validation criteria:**
- [ ] `pnpm run build` completes successfully (no SSR errors)
- [ ] Map renders centered on Pará state
- [ ] 8 location markers visible on map
- [ ] City markers show primary (green) color
- [ ] Battle markers show secondary (terracotta) color
- [ ] Hovering marker shows tooltip with location name
- [ ] Clicking marker opens detail panel
- [ ] Detail panel shows as sidebar on desktop (≥768px)
- [ ] Detail panel shows as bottom sheet on mobile (<768px)
- [ ] Detail panel can be closed
- [ ] Legend explains marker color meanings

---

### Task 8: Fontes Page & Final Polish

**Description:** Create the dedicated bibliography page, add legacy content section, configure SEO metadata, set up Vercel deployment, and perform final quality assurance (Lighthouse audit, accessibility, responsive testing).

**Blocked by:** Task 7

**Implementation guidance:**
1. Create `app/fontes/page.tsx` with:
   - Metadata for SEO
   - Full page layout with Header and Footer
   - Section with all sources grouped by type (Livros, Artigos, Recursos Online)
   - Back link to home (/)
2. Create `components/sections/Legado.tsx` with content about modern legacy:
   - Place names (Avenida dos Cabanos, etc.)
   - Monuments and memorials
   - Annual commemorations
   - Cultural impact
3. Update `app/page.tsx` to import and render Legado section before the fontes preview
4. Update `app/layout.tsx` metadata with comprehensive:
   - OpenGraph (title, description, image, locale: pt_BR)
   - Twitter card metadata
   - viewport settings
   - themeColor (#1a3a2f)
   - keywords for SEO
5. Create `public/robots.txt` allowing all crawlers with sitemap reference
6. Create `app/sitemap.ts` generating sitemap with home (/) and /fontes URLs
7. Update `next.config.ts` with performance optimizations:
   - reactStrictMode: true
   - image formats: ['avif', 'webp']
   - compress: true
   - optimizePackageImports for framer-motion, leaflet
8. Create `vercel.json` with:
   - framework: "nextjs"
   - regions: ["gru1"] (São Paulo)
   - Security headers (X-Frame-Options, X-Content-Type-Options, etc.)
   - Cache headers for fonts and static assets
9. Update `components/layout/Header.tsx` nav to include /#legado link and /fontes link
10. Run Lighthouse audit and fix issues:
    - Lazy load below-fold images
    - Add alt text to all images
    - Verify color contrast meets WCAG AA
    - Check heading hierarchy (h1 → h2 → h3)
    - Optimize any render-blocking resources

**Validation criteria:**
- [ ] `pnpm run build` completes successfully
- [ ] `pnpm run start` serves production build without errors
- [ ] /fontes page displays all sources grouped by type
- [ ] /fontes page has working back link to home
- [ ] Legado section appears in main page with content
- [ ] Header nav includes Legado and Fontes links
- [ ] robots.txt accessible at /robots.txt
- [ ] sitemap.xml accessible at /sitemap.xml (generated)
- [ ] Lighthouse Performance score ≥ 90
- [ ] Lighthouse Accessibility score ≥ 90
- [ ] Lighthouse SEO score ≥ 90
- [ ] No console errors in browser
- [ ] Site is responsive: mobile (375px), tablet (768px), desktop (1280px)
- [ ] All animations respect `prefers-reduced-motion`
- [ ] `vercel` CLI deployment succeeds (or ready for deployment)

## Additional Considerations

### Accessibility
- All images have descriptive alt text
- Keyboard navigation for timeline and map
- `prefers-reduced-motion` respected throughout
- Sufficient color contrast (WCAG AA)

### Performance
- Next.js Image component with blur placeholders
- Lazy loading for below-fold content
- Target: <150KB JS (gzipped), <1.5s FCP

### Future Extensibility
- Content structure supports adding more events/characters via MDX
- Map markers defined in data file, easy to expand
- Design accommodates future illustration/photo assets when available
