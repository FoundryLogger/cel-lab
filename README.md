<p align="center">
  <h1 align="center">🔥 Cel-Lab</h1>
  <p align="center">
    <strong>Procedural cel-shade VFX editor — create stylized shader effects in real-time</strong>
  </p>
  <p align="center">
    Single file · Zero dependencies · Works offline · ~1MB
  </p>
  <p align="center">
    <a href="https://255bit.it">255bit.it</a> · 
    <a href="#features">Features</a> · 
    <a href="#quick-start">Quick Start</a> · 
    <a href="#export">Export</a> · 
    <a href="#use-in-your-project">Integration</a> · 
    <a href="#architecture">Architecture</a>
  </p>
</p>

---

## What is this?

A browser-based procedural VFX editor for creating stylized cel-shade effects — fire, energy, crystals, plasma, organic matter, portals, and anything you can imagine. Design your effect visually with real-time 3D feedback, then export it directly into your game engine or web project.

Everything runs client-side in a single HTML file with Three.js r128 embedded inline. No build step, no npm, no server. Double-click and go.

**→ [Open cel-lab](https://255bit.it/cel-lab)**

---

## Quick Start

```bash
# Download cel-lab.html and open it. That's it.

# Or clone:
git clone https://github.com/foundrylogger/cel-lab.git
cd cel-lab
# Open cel-lab.html in any browser
```

No dependencies. No install. No internet required.

---

## Features

### 🎨 Material System
- **Cel-shade banding** with adjustable thresholds, softness, and edge noise
- **Free color ramp** mode (up to 8 stops) or classic 5-band palette
- **3 independent layers** with per-layer displacement, palette, animation, and blend modes
- **11 base geometries** — Sphere, Cube, Cylinder, Torus, Cone, Icosahedron, Torus Knot, Octahedron, Dodecahedron, Disc, plus custom GLB import
- **3-octave noise displacement** (Simplex, Voronoi, Ridged) with warp, twist, asymmetry, and vertical profiling
- **Shape morphing** between 6 target shapes

### ✨ Lighting & Effects
- Rim light, iridescence, fake subsurface scattering (SSS)
- Emissive patterns (lava veins, energy cracks)
- Procedural overlays (dots, hatching, crosshatch)
- Texture projection (spherical, planar, cylindrical)

### 🎬 Cinematic Post-Processing
- ACES / Filmic tone mapping
- Bloom, god rays, film grain
- Split-tone color grading (shadow + highlight tint)
- Chromatic aberration, vignette, sharpening
- Barrel lens distortion, letterbox, scanlines
- Heat haze, motion trails

### 🔥 Particle System
- Up to 300 GPU-instanced billboard particles
- 4 emission shapes: Point, Ring, Sphere, Cone
- 3D simplex noise turbulence
- Gravity, velocity trail stretching, size-over-life curves

### ⚡ Motion & Destruction
- **Path animation** — Linear, Arc/Throw, Orbit trajectories
- **Flight behavior** — Scale, glow, and spin interpolation
- **Destruction** — Explode (physics fragments + sparks + shockwave), Dissolve (voronoi burn), Implode
- **Impact FX** — Screen shake, bloom flash, expanding shockwave ring

### 🎵 Animation
- **Pulse oscillators** — Per-parameter sine wave animation
- **Keyframe timeline** — Scrub, loop, interpolate between states
- **Bezier curve editor** — Custom easing with presets (ease, bounce, elastic)
- **Audio reactive** — Mic or file input, FFT bands mapped to shader parameters

### 🎲 Intelligent Randomizer
12 archetype system (Inferno, Crystal, Organic, Cosmic, Toxic, Ethereal, Volcanic, Frozen, Electric, Void, Liquid, Mechanical) with color theory palettes and per-archetype feature correlation. Use it as a starting point, then shape the result into your own.

### ◉ SDF Raymarching
Alternative render mode using signed distance fields:
- 5 primitives with smooth boolean operations
- Domain warping (twist, bend, noise)
- Infinite repetition on 3 axes

### 💾 Persistence
- Save/load custom presets with thumbnails (localStorage)
- URL sharing (delta-encoded, one-click)
- JSON import/export for full state

---

## Export

| Format | Description |
|--------|-------------|
| **PNG** | Single frame, up to 2048px |
| **Normal Map** | Auto-generated from displaced surface |
| **PNG + Normal** | Both maps in one click |
| **Spritesheet** | N frames tiled in grid |
| **Strip** | N frames in a single row |
| **Animated GIF** | Adaptive palette + Floyd-Steinberg dithering |
| **PBR Pack** | Roughness, Metallic, AO, Height, Emissive |
| **Godot .gdshader** | Native spatial shader with all parameters |
| **Unity .shader** | ShaderLab + CGPROGRAM, inspector-ready |
| **Three.js module** | ES module with `createCelShadeMaterial()` |

---

## Use in Your Project

### Three.js

Click **📦 Three.js Module** in the Export tab:

```javascript
import { createCelShadeMaterial, updateCelShade, createCelShadeGeometry } from './cel-shade-material.js';

const material = createCelShadeMaterial();
const geometry = createCelShadeGeometry('sphere');
const mesh = new THREE.Mesh(geometry, material);
scene.add(mesh);

function animate() {
  updateCelShade(material, clock.getElapsedTime());
  renderer.render(scene, camera);
  requestAnimationFrame(animate);
}
```

### Godot

Click **🎮 Godot .gdshader** — exports a complete spatial shader with simplex noise, vertex displacement, cel-shading, rim light, and SSS. All parameters as uniforms.

### Unity

Click **🎮 Unity .shader** — exports ShaderLab with CGPROGRAM surface shader. Properties exposed in the Material Inspector.

---

## Architecture

Single HTML file, 3 script blocks:

| Block | Contents | Size |
|-------|----------|------|
| 1 | Three.js r128 (minified, embedded) | 590KB |
| 2 | GLTFLoader (embedded) | 94KB |
| 3 | Application | ~220KB |

16 documented sections covering UI, shaders, animation, particles, post-processing, export, SDF, motion, and persistence. 97% JSDoc coverage, named constants, DRY patterns, error handling.

---

## Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl+Z` | Undo |
| `Ctrl+Shift+Z` | Redo |
| `Scroll` | Zoom |
| `Drag` | Orbit |
| `Esc` | Close dialogs |

---

## Browser Support

- ✅ Chrome / Edge (recommended)
- ✅ Firefox
- ✅ Safari
- ⚠️ Mobile (functional, desktop-optimized)

Requires WebGL 1.0+.

---

## Contributing

Issues and PRs welcome. It's a single HTML file — fork it, break it, make it better.

---

## License

GPL-3.0-or-later — see [LICENSE](LICENSE)

---

<p align="center">
  <a href="https://255bit.it">255bit.it</a>
</p>
