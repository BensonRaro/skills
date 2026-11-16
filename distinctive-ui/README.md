# OpenCode Distinctive UI Reference Library

This package is a reusable design system of **instructions, references, prompts, scripts, and visual inspiration** for OpenCode coding agents.

## Core principle

The agent must not treat the images as category-specific references.

**Every image in `inspiration/images/` is part of one global inspiration pool.**  
For every design task, the agent should inspect the whole pool, identify several compatible visual ideas, combine them, and then adapt them to the requested product instead of copying one image or one category.

The current pool contains dashboard and homepage/marketing references supplied by the project owner.

## Install

Copy these into the root of a project:

- `AGENTS.md`
- `.opencode/skills/`
- `opencode.jsonc` (merge with an existing config rather than blindly replacing it)
- `prompts/`

Keep `inspiration/images/` available to the agent. Do not rename or remove it.

### Windows PowerShell

```powershell
Copy-Item -Recurse -Force .\AGENTS.md <YOUR_PROJECT>\AGENTS.md
Copy-Item -Recurse -Force .\.opencode <YOUR_PROJECT>\.opencode
Copy-Item -Force .\opencode.jsonc <YOUR_PROJECT>\opencode.jsonc
Copy-Item -Recurse -Force .\prompts <YOUR_PROJECT>\prompts
Copy-Item -Recurse -Force .\inspiration <YOUR_PROJECT>\inspiration
```

## Recommended workflow

1. Start OpenCode in the project root.
2. Ask the agent to read `@distinctive-ui`.
3. Give it the page/product to design.
4. Require an **inspiration synthesis pass** before coding.
5. Require a **design-direction decision** before implementation.
6. Require responsive, accessibility, performance, and reduced-motion checks.
7. If imagery is missing, let the agent search the web and prefer Unsplash or another source whose license is verified for the intended use.
8. Never copy another site's identity, exact composition, text, logo, illustrations, or proprietary assets.

## What this library is designed to produce

- Premium SaaS landing pages
- School, hospital, LMS and business management systems
- Dashboards
- Auth and onboarding
- Pricing and feature pages
- Ecommerce listing/detail pages
- Product showcases
- Marketing/editorial pages
- Data-heavy admin interfaces
- 3D/WebGL experiences
- Glass/translucent interfaces
- Dark premium interfaces
- Aurora/mesh gradient systems
- Experimental pages with controlled motion

The goal is **distinctive, production-quality product design**, not a collection of random visual effects.
