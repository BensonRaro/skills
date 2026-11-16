# Production 3D Checklist

Before using 3D:

## Purpose
- What does 3D communicate that a flat image cannot?
- Is interaction necessary?
- Does it improve conversion, understanding or memorability?

## Performance
- compressed textures;
- low-poly/optimized geometry;
- lazy load;
- code split;
- limit post-processing;
- pause when offscreen;
- avoid huge environment maps;
- test on mid-range phones.

## UX
- keyboard/accessible fallback where relevant;
- touch gestures;
- clear affordance;
- loading state;
- no critical information hidden inside canvas;
- reduced-motion fallback.

## Technologies
Use the project's stack. Typical choices include Three.js, React Three Fiber, WebGPU/WebGL, GSAP, Motion, and physics libraries when justified.

Do not add a 3D dependency just because the page is supposed to look futuristic.
