# Verdrobe · Honest Limitations & Future Roadmap

To maintain integrity with engineering teams, recruiters, and technical leaders, this document provides an honest assessment of current technical boundaries and outlines high-impact future enhancements.

---

## 1. Current Limitations

### A. Approximation of Cloth Physics
- **Geometric vs Physical**: Verdrobe evaluates fit geometrically by comparing 3D cross-sectional circumferences against garment circumferences. It does not perform physical finite-element cloth simulation.
- **Fabric Weight & Stiffness**: A stiff 14 oz raw denim jacket and a light viscose silk shirt with identical chest circumferences will behave differently in real life. While Verdrobe incorporates a `stretch` modifier, it does not currently simulate fabric drape stiffness or friction against undergarments.

### B. Reliance on Seller Measurement Accuracy
- **Human Measurement Tolerance**: Sizing calculations depend on sellers correctly measuring clothes flat with a tape measure. A $1.5\text{ cm}$ measuring mistake by a seller results in a $3.0\text{ cm}$ circumference discrepancy on the 3D body.
- **Garment Wrinkling**: If a seller measures an unironed or bunched garment, recorded dimensions will be smaller than actual wearable width.

### C. Anthropometric Domain Boundaries
- **Statistical Model Boundaries**: The Anny statistical body model was calibrated on adult morphologies. While it accurately represents heights between $148\text{ cm}$ and $202\text{ cm}$, extreme anatomical outliers may experience minor mesh vertex extrapolation drift.
- **Posture Invariance**: The 3D body is displayed in a standardized A-pose. Dynamic range-of-motion assessments (e.g. lifting arms or bending knees) are currently communicated via textual tips rather than live skeletal rigging animations.

---

## 2. Future Engineering Roadmap

### Phase 1: Computer Vision Assisted Measuring (Seller App)
- **Problem**: Eliminating human measuring inconsistency.
- **Solution**: Implement mobile camera edge-detection with an A4 paper or coin reference card. Sellers snap a photo of the flat-lay garment, and OpenCV / CoreML automatically extracts pit-to-pit, waist, and length in centimeters with sub-centimeter confidence scores.

### Phase 2: Dynamic Pose Rigging & Skeletal Animation
- **Goal**: Allow buyers to inspect garment tension during movement.
- **Implementation**: Leverage Anny's underlying bone skeleton to toggle between A-pose, sitting, walking, and arm-raising poses, updating vertex tension heatmaps based on joint articulation.

### Phase 3: Brand-Specific Fit Calibration via Buyer Feedback
- **Goal**: Learn real-world brand variance automatically.
- **Mechanism**:
  - Positive feedback loop: When a buyer confirms a garment fit as expected, increment the recommendation confidence score for that brand and silhouette.
  - Negative feedback loop: If buyers report that a specific brand's trousers run tighter in the thigh than stated, the fit engine automatically introduces a learned offset parameter for that brand.

### Phase 4: Social Fit Sharing
- **Goal**: Enable buyers to share their 3D fit maps with friends or sellers for advice before checkout via lightweight WebGL interactive links.
