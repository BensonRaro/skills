# Web Performance

For every visual-heavy page:

- optimize image dimensions;
- use modern image formats where supported;
- lazy-load below-the-fold imagery;
- reserve media dimensions to prevent layout shift;
- split heavy 3D code;
- avoid unnecessary JS animation;
- use CSS transforms/opacity for simple motion;
- pause offscreen effects;
- keep the first viewport useful before heavy assets arrive;
- test mobile performance.

For WebGL/WebGPU, track texture memory, draw calls, shader complexity and frame rate.
