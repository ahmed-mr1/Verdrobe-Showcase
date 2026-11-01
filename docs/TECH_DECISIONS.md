# Verdrobe · Architecture Decision Records (ADRs)

This document captures key technical and design decisions made during the development of Verdrobe, detailing context, decisions, and trade-offs.

---

## ADR 01: NAVER LABS Anny vs SMPL Body Model

### Context
Virtual try-on applications frequently cite SMPL / SMPL-X (Max Planck Institute). However, SMPL's license explicitly prohibits commercial use without prohibitively expensive custom licensing agreements. Furthermore, SMPL libraries require heavy CUDA environments.

### Decision
Adopt **Anny** (developed by NAVER LABS Europe), released under the permissive **Apache 2.0 license**.

### Trade-offs
- **Pros**: 100% legally unencumbered open-source license; compatible with SMPL topology ($13,718\text{ vertices}$); native PyTorch support; efficient parameterization across height, weight, muscle mass, and gender.
- **Cons**: Smaller public community than SMPL; required building custom landmark extraction slices and polynomial regression calibration from scratch.

---

## ADR 02: Skin Fit Heatmap vs 3D Cloth Physics Simulation

### Context
Many fashion tech demos attempt to render 3D garment meshes with cloth physics solvers (e.g. Mass-Spring or Position-Based Dynamics).

### Decision
Render **only the human body in 3D**, and project garment ease as a **contiguous color-coded fit map on the skin**, accompanied by thin 3D boundary line loops (neckline, sleeve ends, hemline).

### Trade-offs
- **Pros**:
  - Consistent **60 FPS WebGL performance** on mobile devices and low-power hardware.
  - No 3D garment scanning or pattern drafting required from sellers—works directly with tape measurements.
  - Zero cloth clipping artifacts or awkward physics glitches.
- **Cons**:
  - Does not show realistic fabric texture, weave drape, or physical folds.
  - Relies on buyers understanding the anatomical heatmapping metaphor.

---

## ADR 03: Decoupled Python Body Service vs Monolithic Node.js 3D Pipeline

### Context
Generating 3D body vertices requires scientific computing libraries (NumPy, PyTorch, SciPy) which are inefficient or unavailable in native Node.js environments.

### Decision
Isolate parametric body fitting into a lightweight **FastAPI Python microservice** running on `127.0.0.1:8000`, proxied seamlessly through Next.js rewrites (`/api/body-service/:path*`).

### Trade-offs
- **Pros**:
  - Utilizes precomputed matrix mathematics (Jacobians, Ridge Regression) with native BLAS/LAPACK acceleration.
  - Keeps the Next.js frontend and API layer lightweight, focused purely on commerce and presentation.
  - Enables horizontal scaling of 3D mesh computation independently of the web frontend.
- **Cons**:
  - Requires maintaining two runtimes in local development (Node.js + Python virtualenv).
  - Addressed with a robust client-side fallback in the TypeScript client that procedurally fits landmark dimensions if the microservice is offline.

---

## ADR 04: Flat-Lay Seller Measurements vs Tag Sizes

### Context
Different apparel brands (e.g., Zara vs Reformation vs COS) define "Size M" completely differently, and pre-loved clothes may shrink or stretch over time.

### Decision
Store and evaluate all garment dimensions using **seller flat-lay measurements in centimeters** (pit-to-pit, waist, hips, total length, sleeve length), converting to circumference using the exact $\times 2$ multiplier.

### Trade-offs
- **Pros**:
  - Standardized ground truth that is immune to brand vanity sizing or tag shrinkage.
  - Mirrors standard high-end resale practices on platforms like Grailed and Japanese archive markets.
- **Cons**:
  - Requires sellers to possess a tape measure. Mitigated with clear SVG visual measuring diagrams in the listing flow.

---

## ADR 05: Neo-Brutalist Visual Design Language

### Context
Many luxury fashion apps use washed-out grey palettes, ultra-thin low-contrast fonts, and hidden menus that introduce significant friction for first-time visitors.

### Decision
Adopt a **high-contrast neo-brutalist design system**:
- Off-white paper background (`#ECE7DC`) paired with deep charcoal borders (`#111111`, 2px solid).
- High-visibility energetic accent colors (`#B6FF3C` electric lime, `#FF6A3D` vibrant orange).
- Strict typography scale with minimum 14px body text, 44px touch targets, and sentence-case readability.
- Clear diverging status colors: Red (tight), Green (balanced), Blue (loose).

### Trade-offs
- **Pros**:
  - 100% WCAG 2.1 AA mathematical color contrast compliance across light and dark themes.
  - Memorable, youthful brand identity aligning with modern streetwear and Gen-Z resale culture.
  - High affordance: buttons look clickable and states are unmistakable.
- **Cons**:
  - More polarizing than generic corporate minimalist e-commerce themes.
