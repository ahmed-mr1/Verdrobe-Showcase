# Verdrobe · Technical Interview Q&A (15 Core Questions)

This document prepares you for technical interviews, system design discussions, and hiring manager deep-dives into the architecture of Verdrobe.

---

### Q1: How do user circumferences become 3D body parameters in the Anny model?
**Answer**:  
We use a two-stage regression and refinement pipeline. Offline, we pre-sampled 3,000 adult morphology configurations from Anny, measured their cross-sections, and fitted a polynomial ridge regression matrix $W$ mapping $(H, C, W, \text{Hips}, S, I, G)$ to Anny's 8 phenotype and local-change parameters. Online, when a user enters measurements, the FastAPI service evaluates this regression in $< 10\text{ ms}$, then performs 3 fast Gauss-Newton iterations using a precomputed $6 \times 6$ sensitivity Jacobian matrix $J = \frac{\partial M}{\partial P}$ to eliminate any residual offset. The final mesh achieves a median absolute error of **0.357 cm** on held-out test scans.

---

### Q2: How does the fit engine decide whether a garment is "tight", "good", or "loose"?
**Answer**:  
The engine compares the garment's circumference against the user's corresponding body circumference to compute **Ease** ($\text{Ease} = \text{Garment} - \text{Body}$). We then evaluate this ease against the garment's declared **Fit Style** (Fitted, Regular, Oversized). For a regular t-shirt, a target ease of $+4\text{ to }+10\text{ cm}$ yields a "Great/Balanced" rating. If ease drops between $+1\text{ and }+4\text{ cm}$, it's classified as "Snug"; below $+1\text{ cm}$ becomes "Tight". If ease exceeds $+12\text{ cm}$, it shifts into "Relaxed" or "Too Loose".

---

### Q3: Why did you choose NAVER LABS Anny over SMPL or SMPL-X?
**Answer**:  
Licensing and production viability. SMPL and SMPL-X from the Max Planck Institute are governed by restrictive academic, non-commercial licenses. Using SMPL in a real-world commercial product requires expensive individual negotiations. Anny, developed by NAVER LABS Europe, is released under the **Apache 2.0 open-source license**, while retaining SMPL-compatible mesh topology ($13,718\text{ vertices}$) and native PyTorch compatibility.

---

### Q4: How is fabric stretch handled in the fit calculation?
**Answer**:  
Garments carry a `stretch` enum (`NONE`, `LOW`, `MEDIUM`, `HIGH`). For woven cotton or rigid denim (`NONE`), zero tolerance is added. For garments with elastane or ribbed knit construction (`MEDIUM` or `HIGH`), the fit engine dynamically expands the acceptable ease thresholds by $+3.5\text{ cm}$ to $+6.0\text{ cm}$. This prevents knit turtlenecks or stretch dresses from prematurely triggering false "Too Tight" red warnings.

---

### Q5: What happens if a user inputs impossible or contradictory measurements?
**Answer**:  
Validation operates at two layers:
1. **Frontend & API Validation**: Numerical bounds clamp inputs within human anatomical minimums and maximums (e.g. Height: $130\text{–}220\text{ cm}$, Waist: $45\text{–}160\text{ cm}$).
2. **Ridge Regression Regularization**: The L2 regularization parameter $\lambda$ in the regression prevents matrix explosion. If an extreme ratio is entered (e.g., $180\text{ cm}$ height with a $45\text{ cm}$ waist), the Jacobian solver clamps parameter updates within $\pm 3$ standard deviations of natural human morphology, preventing distorted or self-intersecting meshes.

---

### Q6: Why did you choose a skin fit heatmap instead of 3D cloth physics simulation?
**Answer**:  
Physics solvers (like Mass-Spring or Position-Based Dynamics) require $5\text{–}30\text{ seconds}$ per frame to resolve collisions, which severely degrades mobile web performance and drains battery. Furthermore, second-hand sellers only provide tape measurements and flat photos—not 3D pattern files. Our contiguous vertex-colored heatmap renders at a silky **60 FPS in WebGL** on any device, providing instant, legible sizing clarity.

---

### Q7: How did you test the application?
**Answer**:  
We maintain a test suite across both runtimes:
- **TypeScript / Vitest (36 unit tests)**:
  - Automated WCAG 2.1 AA mathematical color contrast testing ($L_1/L_2$ formula) ensuring $\ge 4.5:1$ across all light and dark theme elements.
  - Sizing and ease calculator boundary tests.
  - 5-zone fit status classification tests.
  - 3D vertex scaling and status band parity tests.
  - Prisma atomic database transaction tests preventing double-purchases.
- **Python / Pytest (2 integration tests)**:
  - Calibration test verifying that median error on 200 held-out test scans remains strictly below the $0.5\text{ cm}$ SLA threshold.
  - FastAPI endpoint response latency and schema validation.

---

### Q8: How is the 3D Studio organized to prevent visual overload?
**Answer**:  
We organized the layout into a clear 3-column desktop hierarchy (Garment Info $\rightarrow$ 3D Canvas $\rightarrow$ Decision Panel):
1. **Decision Panel Severity Sorting**: Zone rows are sorted by severity, placing tight or loose zones at the top so buyers immediately see what matters.
2. **Expandable Worst Zone**: The specific zone triggering any caveat is automatically expanded with actionable tips (*"Snug at chest: you may feel tension across the front"*).
3. **Pinned Action Bar**: The Buy button is pinned to the bottom of the viewport with the garment price in TND, ensuring a 1-click purchase is always accessible.

---

### Q9: How do you handle dress and skirt lengths on the 3D body?
**Answer**:  
Early iterations mistakenly painted fit status down the legs, making it look like the buyer was wearing colored tights. We fixed this by:
1. Restricting fit status coloring strictly to torso zones down to the hips.
2. Shading the covered area below the hips in a calm neutral drape tone (`#9A958D`) labeled *"Covered (see length)"*.
3. Drawing a thin boundary ring at the calibrated hemline height accompanied by natural language text: *"Ends at your knee"*, *"Ends 4 cm below your ankle"*, or *"Hits the floor"*.

---

### Q10: How does the app prevent double-buying if two users purchase at the same moment?
**Answer**:  
All order creations run inside an atomic Prisma database transaction with immediate status checks. When a purchase request arrives, the transaction checks `WHERE id = garmentId AND status = 'AVAILABLE'`. If available, it updates the status to `SOLD` and generates the `Order` record within the same atomic commit. If another request attempts to buy the same item milliseconds later, the conditional check fails and throws a clean `ALREADY_SOLD` error.

---

### Q11: How does the Next.js frontend communicate with the Python service?
**Answer**:  
We configured Next.js rewrites in `next.config.mjs` mapping `/api/body-service/:path*` directly to the Python FastAPI microservice on `127.0.0.1:8000`. This keeps browser calls same-origin, avoiding CORS preflight latency. Furthermore, the frontend client (`bodyClient.ts`) features client-side caching of loaded OBJ meshes and a procedural mathematical fallback if the microservice is temporarily unreachable.

---

### Q12: What is the continuous improvement feedback loop?
**Answer**:  
When a buyer confirms satisfaction after receiving their purchase, the system records a positive outcome (+1 model accuracy) for that specific brand, fit style, and ease delta. If a buyer reports that an item was tighter than predicted, the feedback pipeline flags that brand's sizing profile, automatically increasing the required ease threshold in future recommendations.

---

### Q13: What were the biggest performance bottlenecks and how did you solve them?
**Answer**:  
The primary bottleneck was initial 3D mesh loading and vertex coloring overhead. We solved this by:
1. Serving pre-indexed OBJ vertex topology cached in browser memory.
2. Replacing dynamic Three.js color arrays with a single contiguous Float32BufferAttribute vertex coloring pass.
3. Decoupling 3D rendering from React state re-renders using Zustand selectors to prevent unnecessary canvas re-mounts.

---

### Q14: What would you build next if you had another month?
**Answer**:  
I would implement **Computer Vision assisted flat-lay measuring** for sellers. Instead of having sellers type numbers manually, they would snap a single top-down photo of the garment on a flat surface with a credit card or sheet of paper for scale. An edge-detection model would automatically trace pit-to-pit, waist, and length, saving sellers time and eliminating measurement error.

---

### Q15: What would you do differently if starting over from scratch?
**Answer**:  
I would build the landmark slicing algorithm directly in C++ / WebAssembly using Emscripten rather than a Python FastAPI microservice. While the Python service is fast (~120 ms), compiling the Anny mesh evaluator and Jacobian refinement to WebAssembly would allow the entire body fitting pipeline to run client-side inside the browser or mobile app with zero server infrastructure costs.
