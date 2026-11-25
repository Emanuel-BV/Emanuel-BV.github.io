---
layout: page
title: "From 3 Months to 3.5 Weeks: Automated Product Digitization & LEGO-Style Builders' Manual"
description: "Turned a 3-month photography bottleneck into a 3.5-week 3-camera studio pipeline, batch-processed an entire PBR texture database in 1 week with Python & Photoshop, and redesigned a 22-page bilingual LEGO-style Builders' Manual."
date: 2025-04-30
category: Engineering Software Utilities
tags: [Engineering Software Utilities, Python & Automation, CAD & 3D Printing, Technical Documentation]
published: true
img: assets/img/projects/cambridge-pavingstones/kitchen-render-stone.png
---

In early 2025, **Cambridge Pavingstones with ArmorTec** faced a classic scaling bottleneck: Marketing and their lead photographer needed to digitize an enormous catalog of pavingstones, wallstones, and color blends—and simply did not have the bandwidth to shoot, color-calibrate, and package every SKU in time.

They originally reached out to me by chance looking for an extra photographer (photography is one of my hobbies). Once I walked the warehouse floor and saw the sheer volume of concrete blocks—many kits spanning **5+ colors, up to 5 block sizes, and 3 surface textures each**—I realized this wasn't just a photography job. It was a **manufacturing throughput and data-pipeline problem**.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html loading="eager" path="assets/img/projects/cambridge-pavingstones/studio-rig-3cameras.jpg" title="The semi-automatic 3-camera warehouse studio rig" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The semi-automatic 3-camera photography station built inside the warehouse: calibrated GVM LED panels, stabilized tripods, white cyclorama backdrop, and an operator loading stone blocks onto the capture table.
</div>

---

## Phase 1: Turning a 3-Month Shoot into 3.5 Weeks

Instead of shooting one stone at a time with a single camera, I proposed and built a **semi-automatic 3-camera capture station** operated like a mini production line:

- **3-Camera Synchronized Rig:** Mounted a **Nikon D5300, Nikon D5600, and Nikon D3500** on weighted tripods paired with **3 remote shutter triggers organized inside a custom 3D-printed control dock**, allowing me to fire all angles rapidly in sequence.
- **Calibrated Constant Lighting:** Installed a full **GVM LED panel** lighting array—one background panel plus three directional side lights—locked to fixed color temperature and manual exposure settings (`RAW`, `F6.3`, `ISO 250`, `1/13s`) so shadows, depth, and surface relief stayed identical across days of shooting.
- **3D-Printed Stone Fixtures & 4-Operator Flow:** Designed and 3D-printed custom low-profile support stands so heavy vertical pavingstones stood upright safely without tipping, coordinating a **4-operator team** rotating products on and off the tables at 3–5 shots per stone.
- **Automated RAW Ingestion:** Configured custom camera naming conventions and wrote a classification script to ingest and sort every RAW batch cleanly into structured product folders automatically.

### Tech Stack & Tools
- **Capture & Hardware:** Nikon D5300 / D5600 / D3500, GVM Calibrated LED Panels, Custom 3D-Printed Trigger Dock & Stone Stands
- **Automation & Imaging:** Python (batch classification, dimension-aware texture/shadow scripting), Adobe Photoshop (color calibration & batch export)
- **CAD & Documentation:** Autodesk Fusion 360 (3D assembly & photorealistic renders), Adobe InDesign (reusable templates), Bilingual SOP Authoring (EN/ES)

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/cambridge-pavingstones/paver-3d-printed-stand.jpg" title="Heavy vertical paver stabilized on custom 3D-printed black stands" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/cambridge-pavingstones/nikon-calibration-screen.jpg" title="Manual exposure calibration on Nikon camera" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Left: Vertical pavingstone stabilized on custom 3D-printed support bases. Right: Fixed manual camera calibration (RAW, F6.3, ISO 250) guaranteeing identical exposure and surface texture depth across every SKU.
</div>

**Result of Phase 1:** A photography project originally projected to take **3 full months** was completed in just **3.5 weeks**.

---

## Phase 2: One-Week Batch Color Calibration with Python & Photoshop

Once the raw photo archive was complete, a second bottleneck appeared: manually color-correcting, cropping, and exporting thousands of stone images would have stalled the project for weeks. The Marketing Director extended my contract so we could solve post-processing as a repeatable pipeline.

- **The Real Challenge:** Every new stone family required fresh white-balance, color, and shadow-depth calibration with the Marketing Director to match the physical product under real light.
- **The Python + Photoshop Solution:** Once a master reference photo for a product line was approved, my **Python + Photoshop batch workflow** propagated that exact calibration profile across the rest of the family and dynamically adapted shadow/texture crops based on each block's physical dimensions.
- **Downstream BIM / Revit Delivery:** The entire catalog was exported into clean, consistently aligned **PNG cutouts and PBR bitmap textures** in just **1 week**, then handed off to a third-party software vendor to build official **Revit and 3D rendering libraries** matching engineering specifications with real product photography.

<div class="row justify-content-sm-center">
    <div class="col-sm-5 mt-3 mt-md-0">
        <figure>
            <img src="{{ '/assets/img/projects/cambridge-pavingstones/paver-batch-pipeline.gif' | relative_url }}" alt="Rapid flipbook of aligned, color-calibrated PNG paver cutouts" title="Rapid flipbook of aligned, color-calibrated PNG paver cutouts" class="img-fluid rounded z-depth-1" width="100%" />
        </figure>
    </div>
    <div class="col-sm-7 mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/cambridge-pavingstones/texture-pbr-warm.jpg" title="Calibrated warm stone PBR texture" class="img-fluid rounded z-depth-1" %}
        <div class="mt-3">
            {% include figure.html path="assets/img/projects/cambridge-pavingstones/texture-pbr-gray.jpg" title="Calibrated gray stone PBR texture" class="img-fluid rounded z-depth-1" %}
        </div>
    </div>
</div>
<div class="caption">
    Left: Animated preview of the aligned, color-calibrated PNG database across multiple blends (Bluestone, Limestone Quarry, Mocha, Onyx-Natural). Right: Resulting PBR bitmap stone textures ready for 3D rendering and Revit.
</div>

---

## Phase 3: Rescuing an Urgent Kitchen Kit Launch & Reinventing the Builders' Manual

During the final week of image processing, an urgent real-world challenge hit: Engineering had developed a new **Pre-Cut & Pre-Packaged Omega Smooth Wall Kitchen Kit** for a special order, and units were already shipping out **without an assembly manual**.

Marketing brought me in for an additional week to act as the technical bridge between **Engineering, the external texture vendor, and Marketing**:

1. **End-to-End Pipeline Validation:** I used this urgent launch as a live proof-of-concept—testing the first PBR texture maps returning from the external software vendor directly inside **Autodesk Fusion 360** to validate how engineering CAD and real stone photography merged.
2. **From Tape Measure & Paper Sketches to Full 3D CAD:** Starting from physical block measurements on the warehouse floor and hand-annotated black-and-white layer sheets, I modeled all **7 construction layers, cut stones, lintels, granite countertops, and stainless-steel appliances** in Fusion 360.
3. **A Brand-New LEGO-Inspired Manual Standard:** Working side-by-side with Marketing, we completely overhauled the company's legacy manual format into a modern, contractor-friendly guide—and I handled the complete engineering-grade **English-to-Spanish translation**.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/cambridge-pavingstones/block-measurement-1.jpg" title="Verifying real block dimensions on the floor" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/cambridge-pavingstones/layer2-paper-sketch.jpg" title="Original hand-annotated paper reference for Layer 2" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/cambridge-pavingstones/fusion360-kitchen-cad.jpg" title="Complete 7-layer assembly modeled in Fusion 360" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Progression from physical block verification (left) and Engineering's hand-marked Layer 2 reference sheet (center) to the full 7-layer parametric Fusion 360 assembly (right).
</div>

### Before vs. After: Upgrading from the Legacy 2024 Manual to the New 2025 Standard

Comparing the legacy [2024 MaytRx Kitchen Manual (v24)](https://www.cambridgepavers.com/dfiles/manuals/MaytRx_Left_Hand_Sided_Kitchen_v24.pdf) against our newly published [2025 Omega Smooth Wall Kitchen Manual (v25)](https://www.cambridgepavers.com/dfiles/manuals/Omega_Smooth_Left_Hand_Kitchen_v25.pdf) illustrates what happens when Engineering and Marketing share a dedicated technical bridge:

- **LEGO-Style Horizontal Full-Color Format:** Replaced cramped vertical black-and-white Word-style pages with a crisp **horizontal full-color layout** featuring consistent corporate branding and navigation footers on every page.
- **Photorealistic Renders Instead of Flat Wireframes:** Replaced dark grayscale solid views with clean, full-color 3D renders and elevation views powered by our newly calibrated stone textures.
- **Instant Block Identification & BOM Tables:** Replaced dense text-only piece lists with clear **`#1`–`#5` & `#2cA`/`#3cA` stone callouts** directly on the blocks plus structured per-layer quantity tables.
- **Upgraded Foundation & Utility Blueprints:** Eliminated sideways-rotated diagrams in favor of clean, properly oriented concrete-base drawings detailing rebar (`#4`), electrical conduit, and plumbing waste-line placement.
- **Engineering-Grade Side-by-Side Bilingual Translation:** Fixed critical machine-translation errors found in legacy manuals (such as unit mismatches and mistranslated construction tools) with clear, parallel English | Spanish columns for field crews.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/cambridge-pavingstones/kitchen-render-stone.png" title="Final photorealistic render - Textured stone finish" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/cambridge-pavingstones/kitchen-render-white.png" title="Final photorealistic render - Omega Smooth finish" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Final 3D renders created in Fusion 360 using the newly digitized stone textures—published directly on the cover and elevation pages of the 2025 Builders' Manual.
</div>

### Official Published Reference
- **New 2025 Bilingual Builders' Manual (22 Pages, REV. 04.2025):** [View Official PDF on CambridgePavers.com](https://www.cambridgepavers.com/dfiles/manuals/Omega_Smooth_Left_Hand_Kitchen_v25.pdf)
- **Legacy 2024 Reference Manual (Before):** [View Legacy v24 PDF for Comparison](https://www.cambridgepavers.com/dfiles/manuals/MaytRx_Left_Hand_Sided_Kitchen_v24.pdf)

---

## Long-Term Impact & Future-Proofing

Beyond meeting the urgent shipping deadline, Marketing and I built **reusable Adobe InDesign master templates** and documented the entire capture, color-calibration, and manual-generation workflow. When the company refreshes its product database again in **4 to 5 years**, future teams will be able to execute the process smoothly without repeating the delays of the first digitization effort.

**Key Achievements:**
- **4x Faster Studio Capture:** Compressed a projected 3-month photography project into **3.5 weeks** via a custom 3-camera rig, 3D-printed fixtures, and a 4-operator flow.
- **1-Week Full-Catalog Export:** Automated color-calibrated PNG and PBR bitmap exports across hundreds of SKUs using Python and Adobe Photoshop.
- **New Corporate Documentation Standard:** Bridged Engineering, Marketing, and external 3D vendors to ship a published 22-page bilingual LEGO-style manual plus reusable InDesign templates.

<div class="row justify-content-sm-center">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/cambridge-pavingstones/emanuel-camera-setup.jpg" title="On-site operating the Nikon studio rig in the warehouse" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Running the calibrated Nikon capture station on the warehouse floor during the 3.5-week sprint.
</div>

---

*Disclaimer: All product names, trademarks, logos, and publicly published manuals referenced in this case study are the exclusive property of Cambridge Pavingstones with ArmorTec. This article documents my independent engineering, photography-rig automation, CAD modeling, and technical documentation contributions completed under a short-term contract (Feb–Apr 2025) and is presented strictly for personal portfolio demonstration. No proprietary source files, raw client assets, or internal databases are shared or distributed.*
