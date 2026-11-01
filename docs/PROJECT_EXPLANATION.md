# Verdrobe · Project Explanation

## Executive Summary
Verdrobe is a specialized second-hand clothing marketplace that eliminates the primary hurdle in online apparel shopping: **fit uncertainty**. By projecting flat garment measurements directly onto a customized 3D human body avatar as an intuitive color-coded fit map, buyers can visualize how pre-loved clothing fits their own physique before buying.

---

## 1. Who is Verdrobe For?

### The Conscious Fashion Buyer
- Loves vintage, archive, and designer second-hand pieces on platforms like Vinted, Depop, or Grailed.
- Suffers from "sizing anxiety": vintage sizes do not match modern tag sizes, and different brands use inconsistent size charts.
- Hesitates to buy because peer-to-peer sellers cannot accept returns. If a jacket is too tight across the shoulders, the buyer is stuck with it.

### The Independent Reseller
- Sells curated pre-owned clothing from their personal wardrobe.
- Spends excessive time answering repetitive buyer messages: *"Can you measure the pit-to-pit?"*, *"How does it fit if I'm 175 cm?"*, *"Is the waist tight?"*.
- Wants a fast listing process where standard flat-lay measurements immediately reassure buyers and accelerate sales.

---

## 2. Why Second-Hand Fashion?

In standard retail e-commerce (such as ASOS or Zara), return rates hover between **25% and 40%**, largely driven by poor fit. While massive retailers subsidize free returns and write off logistics losses, peer-to-peer second-hand platforms **cannot support returns**. 

Every second-hand transaction is final. As a result, fit uncertainty directly suppresses transaction volume. Sizing is the single biggest bottleneck preventing second-hand fashion from replacing fast-fashion purchases.

Verdrobe tackles this exact vulnerability: giving buyers pre-purchase fit confidence so they can buy sustainably without fear of buyer's remorse.

---

## 3. The Core User Journeys

### Journey 1: The First-Time Visitor (J1)
1. **Lands on Home**: Within 5 seconds, understands that Verdrobe lets them see clothes on their own body.
2. **Browses with "Fits You Best"**: Sees immediate listings scored against standard default measurements.
3. **Explores 5-Segment Fit Strips**: Inspects cards at a glance to identify balanced pieces.

### Journey 2: Instant Body Calibration in Under 60 Seconds (J2)
1. **Clicks "My Body"**: Opens a simple onboarding step.
2. **Inputs Measurements**: Enters basic tape measurements (height, bust/chest, waist, hips, inseam) with guided illustrations.
3. **Sees Avatar Live**: The 3D body updates immediately, calibrated to their exact proportions with sub-centimeter anatomical precision.

### Journey 3: The 3D Studio Fit Check (J3)
1. **Enters Studio**: Clicks "See it on my body" on any listing.
2. **Reads the Verdict**: The top card delivers a plain-language summary: *"Great fit. Slightly snug at the shoulders"*.
3. **Inspects the 3D Fit Map**:
   - Green torso bands show comfortable ease.
   - Red warnings highlight tight zones with actionable tips (*"Snug across the chest: consider sizing up for a relaxed drape"*).
   - Hem rings indicate exact vertical lengths (*"Ends 2 cm below your knee"*).
4. **Compares Sizes**: Toggles between available sizes (S, M, L) to choose between a tailored or relaxed silhouette.

### Journey 4: The 3-Click Checkout (J4)
1. **Click 1**: Selects "Buy Now" directly from the pinned Studio bar.
2. **Click 2**: Confirms delivery address and payment in TND with escrow protection.
3. **Click 3**: Completes purchase with atomic database locking, immediately preventing double-buys.

### Journey 5: The 3-Minute Seller Flow (J5)
1. **Photos & Basic Details**: Uploads garment images, brand, condition, and price.
2. **Guided Flat-Lay Measurements**: An interactive SVG diagram guides the seller to lay the garment flat and record straight seam-to-seam numbers (pit-to-pit, waist, hips, length).
3. **Instant Publication**: Listing goes live with precomputed circumferences and fit engine compatibility.

---

## 4. Why Fit Visualization Matters

Traditional virtual try-on tools suffer from two major flaws:
1. **Uncanny Valley 3D Clothes**: Rendering photorealistic 3D fabric with accurate wrinkles and stiffness requires minutes of cloud compute per garment and often looks synthetic or distorted.
2. **Vague Sizing Recommendations**: Standard size recommendation widgets merely say *"You are a Size M (78% match)"*, hiding whether the garment will be tight at the hips or loose at the waist.

Verdrobe shifts the paradigm from **garment simulation** to **anatomical heatmapping**:
- The human body is rendered once in real-time WebGL.
- The garment's ease (garment circumference minus body circumference) is projected as intuitive color bands.
- Buyers receive immediate, unambiguous visual answers to their exact physical questions.
