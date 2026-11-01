# Verdrobe · Live Demo Presentation Script

This guide provides an exact, click-by-click narration script for presenting Verdrobe in technical interviews, portfolio reviews, and recruiter walkthroughs.

---

## 1. The 60–90 Second Perfect Scenario

**Target Time**: 75 seconds  
**Objective**: Demonstrate problem, solution, 3D body calibration, fit heatmap, multi-size comparison, and checkout in under 1.5 minutes.

| Timestamp | Screen / Action | Exact Spoken Words |
| :--- | :--- | :--- |
| **0:00 – 0:12** | **Home (`/`)**<br/>Hover over "Fits you best" row | *"Hi, I'm Ahmed. This is Verdrobe, a second-hand fashion marketplace that eliminates sizing guesswork using parametric 3D body fit maps. In second-hand shopping, buyers don't know if vintage or pre-loved clothes will fit, and sellers can't accept returns."* |
| **0:12 – 0:24** | **My Body Drawer (`Onboarding`)**<br/>Click "My Body", show Sarra's numbers (172 cm, bust 90, waist 72, hips 98) | *"Instead of guessing from tag sizes, buyers calibrate their body in under 60 seconds. Behind the scenes, our Python microservice fits an Anny 3D rigged body mesh to the user's measurements with a measured accuracy of 0.357 cm—less than 4 millimeters."* |
| **0:24 – 0:40** | **Catalog (`/catalog?fitsMe=true`)**<br/>Filter "Fits me", click COS Boxy Tee | *"In the catalog, every listing card has an interactive 5-segment fit strip evaluated in real-time. Let's open this COS Heavyweight Boxy Tee to see how it fits Sarra's body in the 3D Studio."* |
| **0:40 – 0:58** | **3D Studio (`/studio`)**<br/>Show Size M (Green), then switch to Size S (Red) | *"Here in the Studio, we don't do clumsy cloth physics. We project contiguous anatomical fit bands directly on the skin. Size M shows a balanced green fit with 8 cm of ease across the chest. But if we switch to Size S, the chest band immediately turns red. The panel expands the worst zone first with an actionable tip: 'Snug at chest: you may feel tension across the front'."* |
| **0:58 – 1:12** | **Size Comparison & Dress**<br/>Switch to Reformation Dress | *"Buyers can compare S, M, and L side by side to pick their preferred silhouette. And on dresses like this Reformation midi slip, the torso is color-coded while the lower drape remains a calm neutral down to the knee hemline."* |
| **1:12 – 1:20** | **1-Click Buy**<br/>Click "Buy now" on pinned bar | *"Once satisfied, buying is one click with atomic database protection preventing double-buys. That's Verdrobe: sustainable second-hand shopping with zero sizing anxiety."* |

---

## 2. The 2-Minute In-Depth Technical Version

**Target Time**: 120 seconds  
**Objective**: Adds architectural depth on the Python microservice, offline regression calibration, and WebGL shader performance.

### Step 1: Context & The Sizing Dilemma (0:00 – 0:20)
> *"Every year, millions of sustainable fashion transactions fail to happen on platforms like Vinted and Depop because buyers have no return safety net. Vintage tag sizes are notoriously inconsistent, and flat measurements like 'pit-to-pit 49 cm' mean very little to the average shopper. I built Verdrobe to bridge that gap."*

### Step 2: Parametric Body Pipeline (0:20 – 0:45)
> *"The foundation is our parametric body fitting microservice. It uses NAVER LABS Europe's Anny open-source model under the Apache 2.0 license. I trained an offline polynomial ridge regression on 3,000 adult configurations, coupled with active Jacobian sensitivity matrices. When a user enters their measurements, the service refines 13,718 vertices in about 120 milliseconds, delivering a median accuracy of 0.357 cm on our held-out test suite."*

### Step 3: Fast Geometric Ease & Shader Painting (0:45 – 1:15)
> *"Instead of heavy 30-second cloth simulations that crash mobile browsers, our fit engine runs pure geometric ease calculations in TypeScript. We convert flat-lay seller dimensions to circumferences, factor in garment fit style and elastane stretch, and compute five discrete fit states. In Three.js, a custom vertex coloring pass partitions the torso into contiguous anatomical bands with smooth 1.5 cm blending. Uncovered skin stays grey, and dress skirts receive a neutral drape tone down to the calibrated hemline loop."*

### Step 4: Marketplace UX & Production Resilience (1:15 – 1:45)
> *"The marketplace interface is built with Next.js 14 and Tailwind in a high-contrast neo-brutalist theme. We automated WCAG 2.1 AA mathematical color contrast testing to ensure every tag and chip passes a 4.5:1 ratio. For resilience, if the Python service is ever offline, the TypeScript client features a procedural fallback so the 3D Studio never breaks."*

### Step 5: Wrap-up & Engineering Discipline (1:45 – 2:00)
> *"The entire codebase is backed by 36 Vitest unit tests and integration tests, verified with atomic Prisma transactions that guarantee no double-purchases. Everything you see is functional, calibrated, and designed for real-world production performance."*
