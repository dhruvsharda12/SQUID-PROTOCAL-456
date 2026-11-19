# SQUID PROTOCOL // 456

An interactive generative 2.5D canvas artwork and real-time procedural rendering engine built entirely with vanilla JavaScript and the HTML5 Canvas API.

## Features

- **Procedural 3D Geometric Mesh**: Symmetrical low-poly polygonal sculpture computed directly in 3D coordinate space, dynamically projected to 2D with real-time backface culling and Painter's algorithm depth sorting.
- **Dynamic Blinn-Phong Shading**: Real-time cursor-directed lighting engine with ambient base, diffuse reflection, metallic specular highlights, and neon Fresnel rim illumination.
- **Three Visual Atmosphere Modes**:
  - `Mode 01 // Green Light`: High-contrast teal and magenta tones with upward floating embers and geometric glyph particles.
  - `Mode 02 // Red Light — Surveillance`: Crimson telemetry aesthetic featuring CRT scanlines, sweeping horizontal laser radar, and an interactive coordinate tracking reticle.
  - `Mode 03 // Golden Piggy`: Rich gold and violet palette with soft descending bokeh illumination.
- **Interactive Shockwave Rings**: Click or tap to emit expanding geometric glyph pulses (circle, triangle, square).
- **Latent Pattern Discovery**: Move the cursor across the canvas to illuminate hidden radial background filigree patterns.
- **Post-Process Chromatic Aberration**: Horizontal slice displacement and screen-tear chromatic glitch effects.
- **Orbital Telemetry Graphics**: Multi-layered rotating circular HUD with degree ticks and counter-rotating dashed arcs.
- **High-Resolution PNG Snapshot**: Single-click image export saving the current canvas state directly to your computer.
- **Zero Dependencies**: Pure HTML5 Canvas, modern CSS, and vanilla JavaScript with no external libraries or build tools needed.

---

## Interactive Controls

| Input | Action |
| :--- | :--- |
| `1` | Mode 01: Green Light |
| `2` | Mode 02: Red Light (Surveillance) |
| `3` | Mode 03: Golden Piggy |
| `Space` | Trigger Chromatic Glitch |
| `H` | Toggle HUD visibility |
| `Mouse Move / Touch` | Interactive 3D parallax tilt & directional lighting |
| `Click / Tap` | Emit expanding geometric shockwave |
| `Click & Hold` | Overdrive lighting intensity and rotation speed |
| `Save PNG` | Export canvas frame as `squid-protocol-456.png` |

---

## Technical Specifications

### 1. Vector Projection & Parallax
Vertex coordinates are rotated in 3D space using Euler angle transformations driven by smoothed normalized pointer coordinates:

$$\begin{aligned}
x' &= x \cos(\theta_y) + z \sin(\theta_y) \\
z' &= -x \sin(\theta_y) + z \cos(\theta_y) \\
y'' &= y \cos(\theta_x) - z' \sin(\theta_x) \\
z'' &= y \sin(\theta_x) + z' \cos(\theta_x)
\end{aligned}$$

Perspective projection scales coordinates inversely with distance:

$$\text{scale} = \frac{\text{FOV}}{\text{FOV} - z''}$$

### 2. Facet Shading
Each triangular polygon computes surface normals via vector cross-product:

$$\vec{N} = \frac{(\vec{V}_1 - \vec{V}_0) \times (\vec{V}_2 - \vec{V}_0)}{\|(\vec{V}_1 - \vec{V}_0) \times (\vec{V}_2 - \vec{V}_0)\|}$$

Lighting incorporates diffuse dot-product intensity, Blinn-Phong half-vector specular reflection, and grazing-angle Fresnel rim sheens.

---

## How to Run

### Direct Launch
Open `index.html` in any modern web browser.

### Local Server (Optional)
```bash
# Using Python
python -m http.server 3000

# Or using Node.js
npx serve .
```

---

## License

This project is licensed under the [MIT License](LICENSE).
