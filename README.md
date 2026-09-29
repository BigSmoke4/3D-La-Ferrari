# LaFerrari — Walk Around It

> **A cinematic 3D web experience for the Ferrari LaFerrari.**
> Scroll around the car. Explore its form. Repaint it.

<p align="center">
  <strong>WebGL · Three.js · 3D · Scroll Interaction · Creative Frontend</strong>
</p>

---

## ✦ The Experience

**LaFerrari — Walk Around It** is an interactive 3D automotive experience built for the browser.

Instead of presenting a car as a static image, the experience uses a full-screen WebGL canvas and scroll-driven camera movement to create the feeling of walking around a Ferrari LaFerrari in a dark studio environment.

The experience combines:

* Real-time 3D rendering
* Scroll-driven camera choreography
* Interactive paint customization
* Studio-style lighting and reflections
* Responsive layouts
* Smooth motion
* Accessibility-conscious interaction

The interface intentionally stays minimal so that the **car remains the focus**.

---

## ✦ Features

### ◇ Interactive 3D Model

A detailed Ferrari LaFerrari model is rendered directly in the browser using **Three.js and WebGL**.

The model is loaded from an embedded glTF scene and processed at runtime for the experience.

### ◇ Scroll-Driven Walkaround

Scrolling controls a cinematic camera path around the vehicle.

The camera moves through multiple predefined viewpoints, creating a guided walkaround rather than simply rotating the model in place.

### ◇ Paint Studio

Choose from a curated set of Ferrari-inspired paint options:

| Colour             | Hex       |
| ------------------ | --------- |
| Rosso Corsa        | `#d40a1c` |
| Blu Tour de France | `#2350a8` |
| Giallo Modena      | `#f5c400` |
| Verde British      | `#1f4a36` |
| Grigio Titanio     | `#6d7074` |
| Nero               | `#111114` |
| Bianco Avus        | `#e6e3dc` |

The selected colour smoothly transitions across the car's paint material while the surrounding studio environment responds to the chosen tone.

### ◇ Studio Lighting

The scene uses an environment-based lighting setup designed around glossy automotive materials.

The implementation includes:

* HDR-style environment reflections generated from a studio scene
* Directional key lighting
* ACES filmic tone mapping
* sRGB output
* Glossy paint properties
* Clearcoat support

This helps give the bodywork a more realistic automotive finish.

### ◇ Wheel Interaction

The wheel assemblies are identified from the loaded model and grouped around their pivots, allowing their rotation to respond to the experience's movement.

### ◇ Responsive Design

The experience adapts its camera and interface to different screen sizes.

Desktop and mobile layouts use different camera behavior, while the paint dock becomes more compact on smaller screens.

### ◇ Accessibility & Reduced Motion

The experience respects the user's system preference for reduced motion through:

```js
prefers-reduced-motion
```

When reduced motion is enabled, the camera interpolation behavior is adjusted accordingly.

Interactive paint controls also expose accessible labels and pressed states.

---

## ✦ Visual Direction

The interface follows a restrained automotive-editorial aesthetic:

```text
Dark studio
     +
Minimal typography
     +
Full-screen 3D
     +
Subtle glass UI
     +
Cinematic camera movement
```

The typography uses **Bricolage Grotesque**, while the interface relies on a near-black background, muted secondary text, and a small floating paint-control dock.

The goal is simple:

> **Don't compete with the car.**

---

## ✦ Technology

### Frontend

* HTML5
* CSS3
* JavaScript
* Responsive CSS
* Google Fonts

### 3D

* Three.js `r128`
* WebGL
* GLTFLoader
* Meshopt Decoder
* glTF 2.0
* Three.js PMREM environment lighting

The project loads Three.js, GLTFLoader, and the Meshopt decoder directly from CDNs.

### Rendering

* WebGLRenderer
* Antialiasing
* sRGB color output
* ACES Filmic tone mapping
* Environment reflections
* Directional lighting
* Material-based paint customization

---

## ✦ How It Works

The entire experience is designed around a small number of coordinated systems.

### 01 — Scene

A Three.js scene contains the vehicle, camera, lighting, environment, and floor shadow.

### 02 — Model

The LaFerrari glTF scene is parsed at runtime.

The implementation identifies relevant materials such as the car's paint, glass, and wheel components and adjusts them for the experience.

### 03 — Camera

Scrolling is normalized into a `0 → 1` progress value.

That progress value drives the camera through a series of predefined positions and look-at targets.

### 04 — Motion

Camera movement is smoothed using interpolation so that scrolling produces a controlled cinematic movement rather than abrupt jumps.

### 05 — Paint

The paint selector updates the target material colour, while the render loop interpolates toward the selected colour for a smoother transition.

### 06 — Rendering

The scene continuously renders through the browser's WebGL pipeline using Three.js.

---

## ✦ Experience Flow

```text
                  ┌─────────────────┐
                  │    LaFerrari    │
                  │      Hero       │
                  └────────┬────────┘
                           │
                         Scroll
                           ↓
                  ┌─────────────────┐
                  │  Front / Side   │
                  │    Viewpoint    │
                  └────────┬────────┘
                           │
                         Scroll
                           ↓
                  ┌─────────────────┐
                  │ Rear / Engine    │
                  │    Viewpoint    │
                  └────────┬────────┘
                           │
                         Scroll
                           ↓
                  ┌─────────────────┐
                  │ Front Detail    │
                  │    Viewpoint    │
                  └────────┬────────┘
                           │
                         Scroll
                           ↓
                  ┌─────────────────┐
                  │   Paint Studio  │
                  └─────────────────┘
```

---

## ✦ Project Structure

The project is intentionally lightweight.

```text
LaFerrari/
│
├── index.html
└── README.md
```

The experience keeps the HTML, CSS, JavaScript, and glTF scene together inside the main HTML document, making it straightforward to deploy as a static site.

---

## ✦ Running Locally

Because this is a static web experience, no backend is required.

### Option 1 — Open directly

Open:

```text
index.html
```

in a modern browser with WebGL support.

### Option 2 — Local server

For a more reliable development environment, serve the directory using a local HTTP server.

For example:

```bash
python -m http.server 8000
```

Then visit:

```text
http://localhost:8000
```

---

## ✦ Browser Requirements

The experience requires **WebGL**.

If WebGL cannot be initialized, the page displays a fallback message asking the user to use another browser or enable hardware acceleration.

A modern Chromium, Firefox, Safari, or Edge browser with hardware acceleration enabled is recommended.

---

## ✦ 3D Model Attribution

The embedded model metadata identifies the source as:

**Ferrari LaFerrari (Element 6)**
Author: **Echoo**
Source: Sketchfab
License: **CC BY-NC-ND 4.0**

The original model attribution and license information are embedded directly in the glTF asset metadata within the project.

Please respect the original creator's license when redistributing or modifying the project.

---

## ✦ Design Philosophy

This project was built around one idea:

> **Let interaction become the interface.**

There are no complicated menus competing for attention.

There is no traditional product-card layout.

There is no static gallery.

Instead:

**Scroll → Discover → Rotate → Observe → Repaint**

The website treats the 3D model itself as the primary interface.

---

## ✦ Why I Built This

I built this project to explore the intersection of:

**Frontend Engineering × 3D Graphics × Interaction Design**

It was an opportunity to work with browser-based 3D rendering while thinking about:

* Camera choreography
* Material behavior
* Real-time rendering
* Responsive 3D layouts
* Scroll interaction
* Motion design
* Accessibility
* Visual hierarchy

The result is less of a traditional website and more of a **small interactive digital showroom**.

---

## ✦ Future Ideas

Potential directions for the experience include:

* Interior cockpit exploration
* Interactive engine details
* More camera paths
* Configurable wheels and trims
* Additional lighting environments
* Touch-based camera controls
* Performance profiling and optimization
* Mobile-specific interaction patterns

---

## ✦ Credits

**Concept & Development**
Ahanaf Mokammel Omi

**3D Asset**
Ferrari LaFerrari model by Echoo, sourced from Sketchfab.

**3D Engine**
Three.js

**Typography**
Bricolage Grotesque

---

<p align="center">
  Built with curiosity, JavaScript, and a little obsession with beautiful machines.
</p>

<p align="center">
  <strong>Scroll. Explore. Repaint.</strong>
</p>
