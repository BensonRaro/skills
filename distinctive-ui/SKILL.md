---
name: Distinctive UI
description: Design distinctive, production-quality websites and SaaS interfaces by synthesizing the entire visual inspiration library, web research, product UX patterns, motion, 3D, typography, imagery and engineering constraints rather than copying a single reference.
---

# Distinctive UI — Production Design Skill

Use this skill whenever the task involves designing, redesigning, styling, implementing, or reviewing a web UI.

## Mission

Create interfaces that look intentionally designed by a strong product/design team rather than assembled from an AI UI template.

The desired result is:

- memorable but usable;
- visually sophisticated but restrained;
- commercially credible;
- responsive;
- accessible;
- technically realistic;
- original in composition and product expression.

The agent is allowed to combine ideas from many references. It must not clone any reference.

---

# Phase 0 — Understand the product

Before visual design, identify:

1. Product and page purpose.
2. Primary user.
3. Most important action.
4. Information density.
5. Brand personality.
6. Trust/safety requirements.
7. Mobile importance.
8. Whether the page is functional product UI or marketing/experience design.

For school, hospital, LMS and management systems, prioritize information architecture and task efficiency. For marketing pages, product showcases and portfolios, allow more expressive composition and storytelling.

---

# Phase 1 — Inspect the ENTIRE inspiration pool

The local inspiration library is a **global pool**, not a set of page-specific folders.

Inspect recursively:

`inspiration/images/**/*`

Do not stop after finding images that appear to match the requested page type.

Study references across all available groups and extract:

- composition;
- grid behavior;
- typography;
- color relationships;
- contrast;
- spacing rhythm;
- card geometry;
- surface/material treatment;
- imagery;
- chart treatment;
- navigation;
- content density;
- visual hierarchy;
- interaction clues;
- motion clues.

Create a short synthesis such as:

> Reference A contributes the editorial typography.  
> Reference B contributes dashboard density.  
> Reference C contributes the product-display framing.  
> Reference D contributes the dark material language.  
> New design combines those ideas into a different composition.

This synthesis is more important than copying any single screenshot.

---

# Phase 2 — Decide a visual thesis

Choose one primary concept and at most two supporting techniques.

Examples:

- Editorial precision + soft translucent layers
- Dark observatory + luminous data
- Calm clinical interface + spatial navigation
- Luxury commerce + tactile product stage
- Aurora intelligence + dense operational dashboard
- Neo-industrial + restrained glass
- Warm academic + modern data visualization
- Monochrome product system + one energetic accent

Avoid "everything everywhere".

A distinctive design usually has:

- one memorable visual signature;
- one coherent material language;
- one strong typographic hierarchy;
- controlled motion.

---

# Phase 3 — Build the visual system

Define:

## Typography

Use a deliberate role system:

- display;
- heading;
- body;
- metadata;
- numeric/data;
- utility.

Do not use many fonts. Usually one family with a strong weight/size system is enough; a display face may be added only when the concept benefits from it.

Consider:

- optical sizing;
- line length;
- letter spacing;
- variable font axes;
- tabular numerals for data.

## Color

Build:

- base;
- elevated surface;
- subtle surface;
- primary text;
- muted text;
- accent;
- success;
- warning;
- danger;
- focus.

Do not default to purple/blue gradients.

If gradients are used, define their purpose:

- depth;
- lighting;
- brand energy;
- section transition;
- focus.

## Shape

Define:

- radius family;
- border treatment;
- stroke weight;
- control height;
- panel geometry.

Use fewer radii consistently.

## Depth

Choose deliberately among:

- flat;
- soft elevation;
- translucent layers;
- hard-edge panels;
- material stacks;
- spatial 3D.

Do not add shadows to everything.

---

# Phase 4 — Composition

Use composition as the main differentiator.

Possible patterns:

- asymmetric editorial grid;
- oversized type;
- split hero;
- floating product stage;
- horizontal storytelling;
- pinned scroll sections;
- layered canvas;
- bento with one dominant cell;
- dense command center;
- map/spatial UI;
- timeline;
- visual catalog;
- full-bleed image with embedded UI;
- modular dashboard with intentional focal hierarchy.

Do not automatically use:
`navbar + centered headline + two buttons + 3 cards + testimonials`.

---

# Phase 5 — Page-specific behavior

## Marketing landing

Optimize:

- immediate product understanding;
- strong first impression;
- proof;
- feature storytelling;
- conversion.

Use scroll choreography only where it explains or dramatizes the product.

## SaaS dashboard

Optimize:

- scan speed;
- hierarchy;
- task completion;
- data legibility.

Prefer a strong information architecture over decorative cards.

## Authentication

Optimize:

- trust;
- clarity;
- low friction.

A distinctive auth page can use:

- atmospheric background;
- 3D object;
- editorial copy;
- split composition;
- contextual illustration.

But the form must remain the obvious task.

## Onboarding

Use progressive disclosure:

1. orient;
2. collect only essential information;
3. show progress;
4. deliver an immediate useful result.

## Ecommerce listing

Optimize:

- product discovery;
- comparison;
- filters;
- sorting;
- visual rhythm.

Use varied product card proportions when the brand supports it, rather than a monotonous grid.

## Ecommerce detail

Use:

- product stage;
- gallery;
- sticky purchase context;
- material/details;
- social proof;
- shipping/returns clarity.

3D is excellent when it improves product understanding.

## Product showcase

Give the product a "hero object":

- 3D model;
- device render;
- interactive UI;
- cinematic crop;
- exploded view;
- scroll-linked transformation.

---

# Phase 6 — Motion system

Motion must communicate hierarchy or state.

Use:

- entrance choreography;
- section transitions;
- scroll-linked reveals;
- parallax;
- magnetic controls;
- cursor response;
- morphing shapes;
- number transitions;
- progress indicators;
- micro-interactions.

Avoid animation on every element.

Use motion levels:

- Level 0: static;
- Level 1: micro-interaction;
- Level 2: section transition;
- Level 3: immersive scene.

Choose the lowest level that achieves the desired effect.

Always consider:
`prefers-reduced-motion`.

---

# Phase 7 — 3D/WebGL

Use Three.js/R3F/WebGL/WebGPU only when justified.

Good uses:

- interactive product model;
- explorable world;
- data terrain;
- spatial diagram;
- material demonstration;
- hero object;
- interactive storytelling.

Bad uses:

- random spinning blob;
- decorative sphere behind every heading;
- heavy canvas with no interaction;
- 3D that blocks content on mobile.

For production:

- compress textures;
- minimize draw calls;
- use instancing where appropriate;
- avoid huge textures;
- lazy-load 3D;
- provide fallback;
- test on mid-range mobile hardware;
- stop animation when offscreen;
- avoid unnecessary post-processing.

---

# Phase 8 — Imagery

Choose imagery as a system, not a collection of random stock photos.

Useful sources:

- local inspiration assets;
- Unsplash;
- other clearly licensed/open assets;
- generated assets when the project permits them.

Search intent should include:

- subject;
- mood;
- lighting;
- composition;
- crop;
- palette.

Example:
`minimalist modern school architecture warm morning editorial photography`

Do not use a generic "business people smiling" image unless the product genuinely needs it.

---

# Phase 9 — Originality test

Before finalizing, ask:

1. Could this screenshot be mistaken for a generic AI SaaS template?
2. Is there one memorable design decision?
3. Is the memorable decision connected to the product?
4. Does the layout still work without the gradients?
5. Does the UI still work without the animation?
6. Is the inspiration synthesized rather than copied?
7. Does the design have a clear visual hierarchy?
8. Does it look coherent at mobile size?

If answers are weak, redesign the composition before adding more effects.

---

# Phase 10 — Implementation quality

Use the project's existing stack.

Do not introduce a new framework only for visual effects.

Prefer:

- CSS variables/design tokens;
- reusable components;
- semantic HTML;
- accessible controls;
- responsive layout;
- lazy-loaded assets;
- optimized images;
- sensible component boundaries.

Do not hardcode a design in one giant component.

## UI Code Readability & Comments

Add clear, concise comments throughout UI code to identify major sections, components, and important layout decisions (e.g. `// Hero Section`, `// Navigation`, `// Dashboard Overview`, `// Feature Cards`). Explain non-obvious styling, responsive behavior, animations, and complex UI logic, but avoid commenting on obvious code or cluttering every line.

---

# Phase 11 — Final review

Return a concise design audit:

- visual thesis;
- inspiration synthesis;
- implemented signature;
- motion/3D choices;
- responsive decisions;
- accessibility;
- performance;
- remaining risks.

Then iterate on the weakest part instead of adding more decoration.
