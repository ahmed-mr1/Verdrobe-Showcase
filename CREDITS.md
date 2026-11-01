# Verdrobe · Open-Source Credits & Attributions

This project builds on high-quality open-source research, 3D assets, typography, and developer tools.

---

## 1. 3D Body Model & Scientific Libraries

### Anny (NAVER LABS Europe)
- **Project**: Anny (Parametric 3D human body model library)
- **Authors**: NAVER LABS Europe
- **License**: **Apache License 2.0**
- **Repository**: [https://github.com/naver/anny](https://github.com/naver/anny)
- **Role in Verdrobe**: Forms the core parametric geometry generator in `body-service`, defining vertex topology, landmark anchors, and phenotype/local-change deformations.

### MakeHuman / MPFB2 (MakeHuman Community)
- **License**: **CC0 1.0 Universal (Public Domain Dedication)**
- **Role in Verdrobe**: Anny builds on open topological assets originating from the MakeHuman community, completely free of non-commercial academic restrictions.

### Scientific Python Ecosystem
- **PyTorch**: BSD 3-Clause License (The Linux Foundation)
- **NumPy & SciPy**: BSD 3-Clause License (NumPy / SciPy Developers)
- **FastAPI**: MIT License (Sebastián Ramírez)
- **Uvicorn**: BSD 3-Clause License (Encode OSS)

---

## 2. Web & Graphics Stack

### Three.js
- **License**: **MIT License**
- **Authors**: Ricardo Cabello (Mr.doob) and the Three.js Authors
- **Role in Verdrobe**: Client-side WebGL rendering, custom vertex color shaders, camera framing, orbit controls, and boundary line loops.

### Next.js & React
- **License**: **MIT License**
- **Authors**: Vercel, Inc. and React Authors (Meta Platforms, Inc.)
- **Role in Verdrobe**: Full-stack framework, API route handlers, server-rendered layouts, and client hydration.

### Tailwind CSS
- **License**: **MIT License**
- **Authors**: Tailwind Labs, Inc.
- **Role in Verdrobe**: Utility-first CSS styling and custom neo-brutalist design tokens.

### Prisma ORM
- **License**: **Apache License 2.0**
- **Authors**: Prisma Data, Inc.
- **Role in Verdrobe**: Type-safe database queries and atomic checkout transactions.

### Lucide Icons
- **License**: **ISC License**
- **Authors**: Lucide Contributors
- **Role in Verdrobe**: Clean, accessible UI iconography.

---

## 3. Typography & Fonts

### Space Grotesk
- **Author**: Florian Karsten
- **License**: **SIL Open Font License 1.1 (OFL)**
- **Role in Verdrobe**: Primary display headline typography, conveying brutalist precision.

### Plus Jakarta Sans
- **Author**: Gumpita Rahayu (TokyoType Studio)
- **License**: **SIL Open Font License 1.1 (OFL)**
- **Role in Verdrobe**: Primary sans-serif interface typography for body copy, labels, and prices.

### JetBrains Mono
- **Author**: JetBrains s.r.o.
- **License**: **SIL Open Font License 1.1 (OFL)**
- **Role in Verdrobe**: Monospace font used for numeric dimensions, measurements, and code blocks.

---

## 4. Listing Photos & Seed Imagery

### SVG Silhouette Seed Tiles
- **Author**: Created for the Verdrobe demonstration environment (`public/seed/*.svg`)
- **License**: **MIT License / Public Domain**
- **Role in Verdrobe**: Stylized vector flat-lay garment silhouettes with embedded measurement badges, guaranteeing zero broken images and reliable reproducible offline rendering.

### Placeholder Photos & External Listings *(Verification Checklist)*
- ⚠️ **Action for Project Owner**: If you replace the generated SVG seed tiles with photographic catalog images from fashion brands (e.g. COS, A.P.C., Reformation, Ganni), verify their image rights:
  - Prefer images from royalty-free platforms (e.g. Unsplash, Pexels) under free commercial licenses.
  - Or include direct seller fair-use product resale disclaimers as standard on secondary marketplaces.
