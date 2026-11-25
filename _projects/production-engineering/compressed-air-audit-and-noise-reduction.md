---
layout: page
title: "Zero-Budget Compressed Air Audit: Cutting Plant Noise by ~7–8 dB & Modeling $20k/yr in Energy Waste"
description: "Replaced a multi-thousand-dollar ultrasonic vendor quote with an empirical compressor cycle audit across 3 facilities—uncovering 500 CFM in air losses, repairing 27+ leaks, and cutting floor noise for OSHA compliance."
date: 2026-06-15
category: Production Engineering
tags: [Plant Reliability, Energy & Utilities, Safety & OSHA, Root Cause Analysis]
published: true
img: assets/img/projects/compressed-air-audit/air-leak-audit-hero.png
---

*Note: To respect employer confidentiality and legal/NDA boundaries, company names, site locations, internal building identifiers, and facility photographs are intentionally omitted. Facilities are anonymized as Facility A, Facility B, and Facility C, and all charts are reconstructed strictly from anonymized thermodynamic model metrics.*

---

## How It Started: An OSHA Hearing Test & a Price Tag Nobody Would Approve

This project didn't start as an energy initiative—it started as a **workplace safety (OSHA) challenge**.

During routine hearing conservation tests across the production floor, elevated ambient noise levels from saws, machinery, and constant hissing pneumatic leaks raised a clear question in a safety meeting: *What can we fix quickly to lower ambient decibels and reduce OSHA friction?*

Fixing compressed air leaks was the most obvious, practical win. There was just one catch: asking a busy maintenance team to prioritize air leaks purely "for noise" never gained traction. Without a **hard dollar ROI**, leaks always stayed at the bottom of the work-order queue.

Previously, an outside vendor had quoted **thousands of dollars** to bring in ultrasonic cameras, laser detectors, and thermal imaging just to audit the plant—an audit fee that cost more than one or two full months of electricity. Management understandably passed.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html loading="eager" path="assets/img/projects/compressed-air-audit/air-leak-audit-hero.png" title="Multi-facility compressed air leakage and annual energy waste model" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Summary of the empirical compressed-air audit across three anonymized manufacturing facilities: 499.7 CFM in continuous leakage (~80.9 kW wasted), projecting $18.2k–$24.3k/year in electricity waste.
</div>

---

## The Engineering Shortcut: Measuring Air Waste with Only a Stopwatch & Pressure Gauge

Instead of buying expensive ultrasonic gear, I realized the rotary screw compressors themselves (45 kW, 90 kW, and 110 kW) were already giant flow meters.

During **off-hours when every production line was shut down**, any air escaping the header had to be leaks. By timing each compressor's automatic **load (pressurization) vs. unload (decay) cycle across a 20 PSI band (110 to 130 PSI)**, we could calculate exact leakage percentages, wasted CFM, continuous kW draw, and annual dollar cost using straightforward thermodynamics:

1. **Leakage Duty Cycle (% Lost):**
   $$\text{Lost } \% = \frac{T_{\text{charge (+20 PSI)}}}{T_{\text{charge}} + T_{\text{decay (-20 PSI)}}} \times 100$$
2. **Continuous Air Lost (CFM):**
   $$\text{Air Lost} = \text{Rated Compressor Output (CFM)} \times \text{Lost } \%$$
3. **Continuous Wasted Electrical Power (kW):**
   $$\text{kW Lost} = \text{Air Lost} \times \left(\frac{\text{Motor kW}}{\text{Rated CFM}}\right)$$
4. **Annual Energy & Cost Impact** *(20 hrs/day × 250 operating days/year at $0.05/kWh)*:
   $$\text{Annual Cost} = \text{kW Lost} \times 5{,}000\text{ hrs/yr} \times \$0.05/\text{kWh}$$

### Tech Stack & Engineering Methods
- **Methodology:** Compressor Rise/Decay Duty-Cycle Auditing (110–130 PSI), Fluid & Energy Cost Modeling (CFM / kW / kWh)
- **Execution Tools:** Standardized Field Inspection Form (*Air Leak Identification* — component checklist + auditory severity scale), CMMS Root-Cause Taxonomy (`Pneumatic > Air Leak`), Analytical Spreadsheet Modeling

---

## What the Numbers Uncovered Across Three Facilities

Running the timing test across all three buildings produced numbers nobody in leadership expected—especially **Facility B**, where the 90 kW compressor was cycling almost 50/50 just to feed leaks when zero machines were running:

| Metric | Facility A | Facility B | Facility C | **Total / Combined** |
| :--- | :---: | :---: | :---: | :---: |
| **Compressor Rating** | 45 kW / 274.5 CFM | 90 kW / 565.2 CFM | 110 kW / 664.8 CFM | **245 kW / 1,504.5 CFM** |
| **Charge / Decay (110–130 PSI)** | 18 s / 38 s | 7 s / 8 s | 10 s / 35 s | — |
| **Measured Leakage (%)** | **32.14%** | **46.67%** | **22.22%** | **33.2% avg** |
| **Continuous Air Lost** | 88.23 CFM | 263.76 CFM | 147.73 CFM | **499.72 CFM** |
| **Continuous Wasted Power** | 14.46 kW | 42.00 kW | 24.44 kW | **80.90 kW** |
| **Annual Wasted Energy** | 72,321 kWh | 210,000 kWh | 122,222 kWh | **404,543 kWh/yr** |
| **Nominal Annual Cost ($0.05/kWh)** | **$3,616** | **$10,500** | **$6,111** | **$20,227/yr** *(Range: $18.2k–$24.3k)* |

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/compressed-air-audit/rise-decay-methodology.png" title="Rise vs. decay pressure cycle comparison across the three facilities" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Empirical charge vs. decay timing across the 110–130 PSI band: Facility B lost 20 PSI in just 8 seconds with production shut down, exposing a 46.7% continuous leakage load.
</div>

---

## From Spreadsheet to Floor Action: Hunting 40+ Leaks Under a $1,000 Budget

Putting a **~$20,000/year** price tag on wasted electricity immediately unlocked approval to schedule 1–2 maintenance technicians over a weekend—keeping the entire initiative classified as a **Small Project (<$1,000 budget, 1-week cycle)** designed to repeat semi-annually.

To keep execution simple and fast, we applied one pragmatic engineering rule:
> **"Any audible air leak is a leak worth fixing."**

We deployed a standardized **Air Leak Identification** field sheet categorizing each leak by production zone, component type (*Connector, Hose, Cylinder, Valve, Fitting, Pipe*), auditory severity (*Low, Medium, High*), and a photo tag. Walking the floor revealed two clear root-cause patterns:
1. **Moving Assemblies Ate Fittings Alive:** The vast majority of leaks lived on high-cycle moving machine axes where push-to-connect quick fittings wore loose and pneumatic tubing fatigued—often fixed in minutes by trimming clean hose ends or swapping quick connectors.
2. **High-Pressure Pneumatic Punches (>100 PSI):** Pneumatic punching stations operating directly above 100 PSI generated the loudest, sharpest noise spikes whenever seals or valves wept air.

Out of **40+ documented leaks**, the team repaired **~27 accessible leaks** across the first two weekend interventions. The remaining overhead or specialty-part leaks (requiring replacement components or a scissor lift/forklift) were logged cleanly into the CMMS backlog for a third phase.

---

## Real Results—and an Honest Engineering Caveat

- **Immediate Acoustic & OSHA Win:** On the very next Monday morning after the first intervention, ambient floor noise dropped by **up to ~5 dB**, followed by another **2–3 dB reduction** after the second pass (**~7–8 dB total reduction**, dramatically improving operator comfort and hearing-test compliance).
- **Better Engineering Decisions Downstream:** Quantifying our true compressed-air load directly shaped later CAPEX and process projects—for example, rejecting continuous high-CFM air cannons on polymer-cutting lines in favor of lower-consumption static-control alternatives.
- **Honest Note on Long-Term Energy Metering:** While eliminating ~27 major leaks clearly reduced wasted compressor cycling, we could not isolate a clean "after" electric bill baseline: during those exact same months, the facility underwent a major production-floor expansion, adding new automated machinery and two medium backup compressors—pushing total plant power higher due to growth. As a result, the audit's most indisputable realized wins were **acoustic safety (OSHA), operator comfort, and preventive pneumatic reliability**.

---

*Disclaimer: This case study is anonymized to protect employer confidentiality. All figures reflect general thermodynamic auditing methodologies applied to representative multi-facility industrial compressed-air systems; no proprietary company names, locations, layouts, or confidential operational records are disclosed.*
