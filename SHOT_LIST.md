# Verdrobe · Visual Evidence & Shot List

This catalog documents every screenshot captured directly from the live Verdrobe production build. Every shot was captured at high DPI (Desktop 1440x900 @ 2x, Mobile 390x844 @ 3x) without dev overlays, mockups, or post-processing edits.

---

## Desktop Showcase (`screenshots/desktop/`)

### `01_home_hero.png`
- **Caption**: Verdrobe Home Page & "Fits You Best" Recommendation Row.
- **Alt Text**: Verdrobe home screen featuring a bold brutalist headline, intuitive search bar, and personalized garment recommendations matched to Sarra's measurements.
- **What it proves**: Shows clear brand positioning, immediate value proposition for first-time visitors, and real-time personalized fit scoring on the marketplace feed.

### `02_catalog_fit_strips.png`
- **Caption**: Marketplace Catalog with Active "Fits Me" Filter and 5-Segment Fit Strips.
- **Alt Text**: Marketplace listing catalog showing filter sidebar, price range up to 200 TND, category chips, and 5-segment fit chips on every product card.
- **What it proves**: Proves that fit computation runs efficiently across multiple listings simultaneously, displaying micro fit status strips without requiring the user to open individual product pages.

### `03_onboarding_body_setup.png`
- **Caption**: Interactive Body Setup Wizard and Anatomical Measuring Guide.
- **Alt Text**: Two-column onboarding modal showing height, chest, waist, hips, and inseam input fields with an anatomical measuring diagram.
- **What it proves**: Demonstrates rapid, user-friendly body setup in under 60 seconds with plain-language inputs and zero confusing technical jargon.

### `04_studio_hero_great_fit.png` (HERO SHOT)
- **Caption**: 3D Fit Studio Hero View – Balanced Fit on COS Heavyweight Tee (Size M).
- **Alt Text**: Three-column 3D Studio showing the full-height 3D avatar with green contiguous fit bands, natural language verdict headline "Great fit across chest and shoulders", and zone ease breakdowns.
- **What it proves**: Demonstrates the core technical innovation: contiguous vertex color projection directly on the skin, clear diverging color semantics (green = good), and readable hierarchy.

### `05_studio_tight_item.png`
- **Caption**: 3D Fit Studio – Snug / Tight Fit with Actionable Advice (COS Boxy Tee, Size S).
- **Alt Text**: 3D body viewer showing red fit bands across the chest and shoulders with an expanded worst-zone warning card and styling tip.
- **What it proves**: Proves worst-zone severity sorting in the decision panel and actionable guidance ("Snug at chest: you may feel tension across the front when moving").

### `06_studio_loose_item.png`
- **Caption**: 3D Fit Studio – Relaxed / Loose Fit (COS Boxy Tee, Size L).
- **Alt Text**: 3D body viewer displaying blue fit bands across torso and chest zones indicating ample ease (+16 cm).
- **What it proves**: Demonstrates the diverging color scale (blue = loose, light blue = relaxed) and how oversized garments are communicated clearly to buyers.

### `07_studio_dress_hem.png`
- **Caption**: 3D Fit Studio – Midi Dress with Continuous Covered Drape and Hem Landmark.
- **Alt Text**: 3D avatar wearing Reformation Juliette Linen Dress showing calibrated torso fit bands, neutral covered shading below hips, and a thin hemline ring at knee height.
- **What it proves**: Proves the fit map distinguishes between fitted torso zones and open drapes: dress skirts are shaded in a calm neutral drape tone rather than false fit colors, with natural hemline phrasing.

### `08_studio_trousers.png`
- **Caption**: 3D Fit Studio – Trouser Fit on A.P.C. Selvedge Jeans (Size M).
- **Alt Text**: 3D avatar showing waist and hip fit status alongside calibrated leg inseam length.
- **What it proves**: Demonstrates bottom category adaptation: torso remains neutral while waistband and hip ease are highlighted alongside ankle break position.

### `09_studio_zone_hover.png`
- **Caption**: Interactive Zone Highlighting on 3D Body Mesh.
- **Alt Text**: Hover state on the Chest measurement row causing the corresponding chest band on the 3D body to illuminate.
- **What it proves**: Shows bidirectional communication between DOM controls and the Three.js WebGL canvas.

### `10_compare_sizes_combined.png`
- **Caption**: Multi-Size Fit Map Progression (Size S vs M vs L on Same User).
- **Alt Text**: Side-by-side comparison showing Size S (snug red chest), Size M (balanced green fit), and Size L (relaxed blue fit) on Sarra.
- **What it proves**: Demonstrates how buyer sizing uncertainty is eliminated: buyers immediately see how sizing up or down shifts the ease from snug to relaxed.

### `10a_compare_size_s.png`, `10b_compare_size_m.png`, `10c_compare_size_l.png`
- **Caption**: Individual high-resolution captures for each size in the progression.
- **What it proves**: Raw un-stitched captures of the individual size states.

### `11_two_bodies_response.png`
- **Caption**: Morphological Responsiveness – Petite (158 cm) vs Tall (184 cm) Avatar.
- **Alt Text**: Side-by-side comparison of the same Size M garment fitted onto a 158 cm petite avatar and a 184 cm tall athletic avatar.
- **What it proves**: Proves the 3D avatar is not a static 3D mesh: it dynamically scales its anatomical vertex positions to reflect real user height, circumferences, and body shape.

### `11a_body_petite.png`, `11b_body_tall.png`
- **Caption**: High-resolution individual captures of the petite and tall body configurations.
- **What it proves**: Individual full-resolution raw captures of the distinct body phenotypes.

### `12_item_page_fit_view.png`
- **Caption**: Marketplace Listing Detail Page with Embedded Fit Summary.
- **Alt Text**: Listing page for COS tee showing price in TND, seller profile, condition badge, seller flat-lay measurements, and quick link into 3D Studio.
- **What it proves**: Seamless integration between traditional e-commerce listing details and the 3D fit visualization engine.

### `13_sell_form_flat_lay.png`
- **Caption**: Seller Listing Form with Flat-Lay Measuring Diagram.
- **Alt Text**: Step 3 of the listing creation form showing an SVG garment diagram indicating where pit-to-pit, waist, hips, and length must be measured flat.
- **What it proves**: Proves that seller data entry is intuitive, fast, and structured to capture the exact flat dimensions needed by the fit engine.

### `14_orders_page.png`
- **Caption**: Orders Page & Transaction Confirmation.
- **Alt Text**: Orders table showing completed purchase with price in TND, buyer protection tag, and verified seller identity.
- **What it proves**: Demonstrates the end-to-end commerce transaction flow with atomic database locking and order tracking.

### `17_garment_shape_toggle.png`
- **Caption**: Studio Mesh Shell Overview.
- **Alt Text**: 3D body viewer showing complete anatomical framing head-to-toe with studio lighting and soft contact floor shadow.
- **What it proves**: Shows full body framing with head, hands, and feet clearly anchored on the ground plane.

### `18_terminal_tests_and_calibration.png`
- **Caption**: Automated Test Suite Verification and Anny Calibration Report.
- **Alt Text**: Terminal window showing 36 passing Vitest unit tests, 2 passing Pytest integration tests, and 0.357 cm median calibration error.
- **What it proves**: Authentic proof of code quality, WCAG AA compliance, and anatomical precision measured against held-out empirical data.

---

## Dark Theme Showcase (`screenshots/dark/`)

### `16_studio_dark_theme.png`
- **Caption**: 3D Fit Studio in High-Contrast Brutalist Dark Theme.
- **Alt Text**: Studio rendered with rich obsidian backgrounds, high-contrast borders, neon lime accents, and vibrant fit heatmap on the body.
- **What it proves**: Proves seamless light/dark mode theming across both the 2D UI components and the Three.js 3D lighting environment, maintaining WCAG AA contrast throughout.

---

## Mobile Showcase (`screenshots/mobile/`)

### `15a_mobile_home.png`
- **Caption**: Mobile Home Screen (390x844).
- **Alt Text**: Mobile home screen showing search, brand filter pills, and product recommendation cards.
- **What it proves**: Shows responsive mobile layout with touch-friendly 44px hit targets.

### `15b_mobile_studio_sheet.png`
- **Caption**: Mobile 3D Studio with Draggable Bottom Sheet.
- **Alt Text**: Mobile Studio showing the 3D body canvas occupying the upper screen while the verdict and zone details rest in an interactive bottom sheet.
- **What it proves**: Proves mobile-optimized viewport utilization: users interact with the 3D canvas and pull up the decision drawer seamlessly.

### `15c_mobile_item_page.png`
- **Caption**: Mobile Listing Detail Page.
- **Alt Text**: Mobile product page with photo gallery, seller info, and sticky bottom action bar.
- **What it proves**: Complete e-commerce functionality adapted for mobile screens.

### `15d_mobile_onboarding.png`
- **Caption**: Mobile Body Onboarding Drawer.
- **Alt Text**: Mobile slide-over drawer allowing quick body measurement entry.
- **What it proves**: Rapid onboarding accessible on touch devices without layout breakage.
