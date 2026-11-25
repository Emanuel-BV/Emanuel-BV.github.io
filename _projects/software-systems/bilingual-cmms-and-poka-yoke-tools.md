---
layout: page
title: "In-House Bilingual CMMS & Shop-Floor Poka-Yoke Web Suite"
description: "Architected a relational bilingual CMMS piloted in high-volume manufacturing alongside QR-code downtime tracking, ERP integration, and interactive Low-E & 5S web tools."
date: 2026-08-01
category: Software Systems
published: true
---

*Note: To protect employer confidentiality (NDA), internal URLs, proprietary plant photos, and customer data are omitted. This case study focuses on software architecture, data modeling, and Lean/Poka-Yoke engineering principles.*

---

## The Challenge

In high-volume discrete manufacturing, maintenance teams frequently operate in a reactive mode: equipment stops are reported verbally, spare parts are untracked across buildings, and language barriers between bilingual floor technicians and management slow down troubleshooting and root cause analysis. Off-the-shelf SaaS CMMS tools can also carry steep recurring license costs while remaining rigid against legacy plant ERPs.

---

## 1. Bilingual In-House CMMS ("Maintenance Way" — Building 21 Pilot)

In collaboration with IT and Maintenance leadership, I architected and deployed an in-house **Computerized Maintenance Management System (CMMS)** piloted in **Building 21** (currently tracking operational results ahead of multi-plant expansion):

- **Normalized Relational Data Model:** Structured clean relational schemas separating `Assets`, `MachineTypes`, `MachineStatuses`, `LocationBuildings`, `SpareParts`, `WorkOrders`, and `DowntimeLogs`.
- **Floor-Level QR Downtime Tracking:** Technicians and operators scan machine-specific QR codes from mobile tablets to log faults immediately—splitting elapsed downtime into **Waiting Time** vs. **Active Repair Time (`HH:MM`)** and capturing mandatory diagnostic photos.
- **Role-Based Andon Dashboard:** Designed a responsive, high-visibility Light-Mode interface tailored to six operational roles (*Technician, Leader, Line Manager, Production Manager, Engineer, Director*) with real-time Andon status indicators (*Active, Pending Check, In Repair, Stopped, Offline*).
- **Cognate Bilingual UX & ERP Bridge:** Engineered the interface around English–Spanish cognate terminology to maximize technician adoption, integrated with the plant's manufacturing ERP (**Fenevision**) and structured **"5 Whys"** root cause analysis workflows.

```text
[Machine QR Code] ──▶ [Mobile Fault Form (EN/ES)] ──▶ [Relational DB: Assets / WOs / Parts]
                                                                    │
         ┌──────────────────────┬───────────────────────────────────┤
         ▼                      ▼                                   ▼
 [Real-Time Andon UI]   [ERP / Fenevision Sync]          [5 Whys RCA & KPI Reports]
 (6 Role Views, HH:MM)  (Production & Asset Context)     (Waiting vs. Repair Time)
```

---

## 2. Shop-Floor Poka-Yoke & 5S Web Utilities

Alongside the CMMS, I developed lightweight, zero-install **HTML5 / CSS3 / Vanilla JavaScript** web applications designed specifically for shop-floor tablets and large-format 11"x17" Ledger printouts (`@media print` / CSS Paged Media):

- **Interactive Optical Low-E Coating Visualizer:** Dynamically renders double- and triple-pane insulated glass anatomy (showing Argon fill, obscure glass, and exact red indicator lines on surfaces #1–#4 for commercial Low-E coatings such as CG70, CG55, 8071, and IS20) to eliminate operator orientation errors.
- **5S Rack & Cart Label Generator:** Real-time browser tool producing color-coded, high-contrast cart signage readable from >10 meters away with built-in guillotine crop marks for lamination.
- **Standardized Bilingual SOP & Lubrication Matrix Framework:** Modular HTML-to-PDF SOP templates and a 6-lubricant color-coded compliance ledger (`LUB-01` to `LUB-06`) enforcing elastomer and air-line compatibility.

---

### Tech Stack & Engineering Methods
- **Software & Data:** Relational Database Modeling (SQL/CSV Normalization), HTML5, CSS3 (Grid, Flexbox, CSS Paged Media), Vanilla JavaScript, Excel VBA, Fenevision ERP Integration
- **Lean & Reliability:** CMMS Architecture, QR-Code Andon Tracking, 5 Whys Root Cause Analysis, Poka-Yoke Visual Management, 5S Standardization
