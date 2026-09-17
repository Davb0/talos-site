# Project Talos — project site

A single-page site for **Project Talos**, a tracked ground-to-air tracking robot: a two-axis
camera turret that holds a moving aerial target in frame while the chassis turns to keep
the turret inside its range.


## What's on the page

- **Turret loop** — a live simulation of the pan/tilt PID loop, running the real constants
  from `backend/config.py` (Kp 0.045 / Ki 0.0005 / Kd 0.012, 12 px deadzone, EMA α 0.35,
  3.5°/frame step clamp, chassis assist at 30° with hysteresis). Move the pointer over the
  frame to fly the target.
- **CAD viewer** — the chassis tub, the Jetson mounting platform and the Jetson developer
  kit, in interactive 3D. Geometry is exported from the project CAD, quantized to 16-bit
  coordinates and embedded in the page, so nothing is fetched at runtime.
- **Remote ID cueing (planned)** — an ESP32-C6 receiver decodes drone Remote ID broadcasts so
  the Jetson can point the turret before the camera sees the target; indoor stand demo with a
  test transmitter, outdoor GPS-aimed version on video.
- **Why it matters** — documented drone incursions (Gatwick, Copenhagen, Munich, Tulcea,
  prisons, wildfires) with sources, plus six realistic roles for a cheap detect-and-track unit.
- Tracking pipeline, turret control, system architecture, bill of materials and build log.

## Running it

It is one self-contained file. Open `index.html`, or serve the folder:

```bash
python3 -m http.server 8080
```

The only external requests are Google Fonts and three.js from cdnjs.

## Deploying to GitHub Pages

Settings → Pages → Source: *Deploy from a branch* → `main` / `/ (root)`.
`.nojekyll` is present so Jekyll leaves the file alone.
