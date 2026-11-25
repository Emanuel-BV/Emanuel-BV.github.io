---
layout: page
title: "Fault-Redundant High-Mountain IoT Weather Station (Open-Source)"
description: "Designed, built, and field-validated an open-source, modular IoT weather station for extreme high-mountain ecosystems—featuring dual power/data redundancy, IP68/IP67 protection, and sub-zero testing."
date: 2021-06-01
category: Custom Machinery Design
tags: [Embedded & IoT, Hardware Design, CAD & 3D Printing, Open Source]
published: true
img: assets/img/projects/iot-weather-station/field-deployment-mountain.jpg
---

This project began in meetings with the **Páramo Research Group at EIA University** in Colombia. Researchers studying high-altitude mountain ecosystems kept running into the exact same wall with commercial weather stations: they were **closed ecosystems** costing millions of pesos that only worked with proprietary manufacturer sensors, locked down sampling intervals, and refused to integrate custom experimental instruments built by university labs—such as sensors for **horizontal fog-water mass transfer** or **soil thermal flux**.

Worse yet, many existing remote loggers had no affordable near-real-time telemetry (this was before Starlink existed, when Iridium satellite plans were financially out of reach for academic teams). Scientists had to hike back into remote mountains months later just to retrieve data—only to discover too late that a dead battery, condensation short, or corrupted onboard flash memory had wiped out months of irreplaceable fieldwork.

For my **Mechatronics Engineering Capstone Thesis** (advised by Prof. Alejandro Puerta Echandía), I set out to engineer an **open-source, modular, fault-redundant IoT weather station**—and document every engineering trade-off so future engineers and research teams wouldn't have to build one from scratch.

<div class="row justify-content-sm-center">
    <div class="col-sm-7 mt-3 mt-md-0">
        {% include figure.html loading="eager" path="assets/img/projects/iot-weather-station/field-deployment-mountain.jpg" title="Weather station deployed at 2,911 m.a.s.l. in Reserva Ecológica San Sebastián de la Castellana" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The completed IoT weather station camouflaged in high-mountain vegetation during field deployment at 2,911 m.a.s.l. (Reserva Ecológica San Sebastián de la Castellana, Colombia).
</div>

---

## Designing for Harsh Reality (and a Pandemic Pivot)

Following **Karl T. Ulrich's product development methodology** alongside **IDEAM, WMO, and NOAA** meteorological standards, I evaluated three complete system architectures (Raspberry Pi Zero + Iridium Satellite vs. Arduino Due + GPRS vs. **Adafruit Feather M0 Adalogger + GPRS/GSM/GPS + Deep-Discharge Solar Storage**) through a weighted morphological decision matrix.

When the **COVID-19 pandemic** shut down university industrial workshops and suspended all expeditions above 4,000 m.a.s.l. (glaciers and high páramos), we adapted intelligently rather than stalling:
- We pivoted field testing to **2,700–2,911 m.a.s.l.** right below the páramo treeline—trading below-freezing outdoor air for **relentless constant humidity**, while validating sub-zero electronics and battery endurance inside a **-5°C thermal chamber** (24V F40C4TMP refrigerator).
- We also prioritized **stealth integration with nature** (low-profile dark enclosure to prevent theft/human tampering—a documented cause of failure on public Colombian stations) and **portability**, ensuring **1 to 2 people** could hike in and deploy the station in under **30 minutes**.

### Tech Stack & Core Hardware
- **Controller & Firmware:** Adafruit Feather M0 Adalogger (32-bit ATSAMD21), C/C++ (custom `SERCOM` UART `Serial2`, `TinyGPS++`, `Adafruit_MQTT_FONA`, `SleepyDog` low-power watchdog)
- **Telemetry & Cloud:** 3G/GPRS cellular MQTT + GSM SMS emergency alerts, NEO-6M GPS, Adafruit IO live dashboard (CSV export + Leaflet GPS map)
- **Open Sensor Bus:** 6 analog channels (A0–A5), I2C (tested with SHT31), Serial UART, and internal DHT21 health monitor wired through waterproof **GX-12 / GX-3** aviation connectors
- **Power & Enclosure:** 15W+ aluminum-frame solar panel, 12V deep-discharge primary battery + 2500mAh Li-Ion auxiliary backup, IP68 hard case + inner IP67 ABS "black-box" vault with custom **PETG 3D-printed** brackets

---

## Inside the "Aircraft Black-Box" Architecture

To make the station resilient against water ingress, drops, and component failures, I engineered a **nested two-stage enclosure**:

1. **Outer IP68 Power & Distribution Vault:** A reinforced polypropylene security case lined with custom-cut fire-retardant foam housing the 12V deep-discharge primary battery, a solar charge controller mounted on a **3D-printed removable slide rail**, a universal terminal-block PCB for rapid field diagnostics/repairs, waterproof GX bulkhead connectors, external cellular antenna extension, and **200g of indicator silica gel** to prevent condensation below 15°C.
2. **Inner IP67 Electronics "Black Box":** Inspired by aircraft flight recorders, the Feather M0, MicroSD logger, auxiliary Li-Ion battery, GPRS/GSM modem, and GPS module live inside a sealed secondary ABS box strapped inside the outer case—held rigidly by three interlocking **PETG 3D-printed brackets** modeled in CAD.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/iot-weather-station/cad-petg-brackets.jpg" title="CAD design of interlocking PETG 3D-printed electronics mounts" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/iot-weather-station/cad-electronics-enclosure.jpg" title="Complete electronics assembly nested inside the IP67 ABS inner enclosure" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Custom CAD assembly of the interlocking PETG 3D-printed brackets holding the Feather M0, auxiliary Li-Ion battery, GPRS-GSM, and GPS modules inside the sealed IP67 inner "black box."
</div>

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/iot-weather-station/open-case-internals.jpg" title="Completed internal layout inside the IP68 field case" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Completed modular interior: inner IP67 electronics vault (left), terminal-block breakout PCB with waterproof GX connectors (center), 12V primary battery (right), solar controller on 3D-printed rail (top right), and silica gel humidity control.
</div>

---

## Multi-Layer Fault Redundancy & Self-Diagnostics

Every critical failure mode identified in real mountain deployments was paired with an automatic fallback:

- **Dual Power + Automatic Safe Mode:** If the 12V primary battery drops below 20% (or is disconnected), the Feather seamlessly switches to its onboard **2500mAh Li-Ion auxiliary battery**, triggers `SleepyDog` low-power sleep, pauses high-draw GPRS uploads, continues logging locally to MicroSD, and sends **SMS emergency alerts with its latest GPS coordinates** every 8 hours—providing **3 to 5 days of survival margin**.
- **Dual Data Storage:** Sensor readings stream via **MQTT** to an **Adafruit IO** cloud dashboard while simultaneously writing sequentially numbered `.TXT` files (`BATE0000.TXT`) to the local MicroSD card with GPS timestamps—plus LED blink-code diagnostics on boot if card initialization fails.
- **Internal Health Watchdog:** An internal **DHT21** sensor continuously monitors enclosure health, firing SMS alerts if internal humidity exceeds 90% (leak/condensation), temperature exceeds 40°C (short/overheat), or drops below 5°C (freeze/hail risk).

---

## Real Engineering Obstacles Caught & Solved in Testing

Building the physical hardware exposed four subtle problems that only show up during real testing:

1. **Voltage-Divider EMI Noise:** Reading the 12V primary battery via an analog voltage divider introduced electromagnetic noise, which I attenuated cleanly with a **0.03 Hz band-pass filter**.
2. **GPRS Current-Spike Brownouts:** During auxiliary battery discharge tests below 3.8V, peak GPRS transmission current starved simultaneous MicroSD writes. Doubling the auxiliary Li-Ion cell in parallel resolved the brownout (with a 4×4700 µF capacitor bank documented for future revisions).
3. **RF Attenuation Inside the Hard Case:** Moving the GPRS antenna outside the polypropylene shell via a sealed bulkhead extension restored stable cellular telemetry even under heavy forest canopy and rain.
4. **Storm Telemetry Blackout (Redundancy Proven Live):** During field deployment at 2,911 m.a.s.l., electrical storms caused two GPRS dropouts totaling **3 hours of lost cloud transmission**—and **zero data was lost** because the MicroSD backup seamlessly filled the gap.

---

## Validated Results & Open-Source Impact

- **Power Endurance:** Primary battery delivered **7.5 days** of continuous autonomy without solar input, recharged from 20% to 100% in **1 sunny day** (13–15W) or 2–3 rainy days (7–10W), and lost only **25.7%** over **4 full weeks at -5°C** with zero capacity degradation upon recharge.
- **Field Performance (2,911 m.a.s.l.):** Primary battery never dropped below **53% (12.6V)** and reached 100% charge on **86% of days** (between 2:00–4:00 PM); the auxiliary battery remained at 100% reserve the entire deployment. Internal temperature stayed between **7°C and 28°C**, and internal humidity remained **below 63%** (confirmed visually as the 200g silica gel shifted from dry blue to pink).
- **Rapid Deployment & Open-Source Legacy:** Transportable and deployable in **under 30 minutes** with basic tools. Published fully open-source through EIA University's repository so future engineering students and research teams can adapt the hardware, code, and decision matrices directly.

### Official Published Thesis
- **EIA University Institutional Repository (June 2021):** [Development of Weather Station with IoT, Redundant to Failures and for High Mountain Environmental Conditions](https://repository.eia.edu.co/handle/11190/3386?locale-attribute=en)
