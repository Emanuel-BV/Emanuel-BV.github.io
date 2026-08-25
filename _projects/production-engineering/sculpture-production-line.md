---
layout: page
title: "Sculpture Production Line: Scaling with Large-Format 3D Printing"
description: "By integrating large-format 3D printing and modernizing a traditional workshop, a complete workflow was engineered for the design, quotation, manufacturing, and painting of batch sculptures."
img: assets/img/projects/sculpture-production/rabbit.jpg
importance: 1
category: Production Engineering
---

In 2021, a traditional sculpture workshop faced a significant bottleneck when tasked with producing large, lightweight props for theatrical and audiovisual productions. Standard materials like ceramics, clay, or wood were either too fragile or too heavy, heavily inflating transport and production costs. The ultimate goal was to manufacture durable, lightweight props that a warehouse could easily rent out for events and audiovisual productions across the city.

To address this challenge, I was brought in to engineer a complete batch production line. By introducing a custom 1m³ large-format 3D printer and establishing a standardized workflow—spanning from 3D design and quotation to printing, post-processing, and airbrushing—we fundamentally transformed their operations.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html loading="eager" path="assets/img/projects/sculpture-production/rabbit.jpg" title="Final painted sculpture" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    One of the many high-quality batches produced using the new workflow.
</div>

## The Workflow Solution

To transition the workshop into a highly efficient mini-factory, we structured the workflow into distinct, manageable stages.

The process began with the workshop owner handling quotations and client requirements. These requirements were then passed to a 3D designer using **Autodesk Maya 3D** to create the initial sculpture models. Once the STL files were ready, they were processed in **UltiMaker Cura** and sent to the 3D printing farm.

### Tech Stack & Materials
* **Design & Slicing:** Autodesk Maya 3D, UltiMaker Cura
* **Manufacturing:** Custom 1m³ Large-Format 3D Printer, 50x50x50cm secondary printers
* **Materials:** PLA, PETG, Fiberglass, Resin, Primer, Airbrush Paints
* **Hardware Tooling:** Heat guns, vibratory polishers with water misting adapters

## 3D Printing Production

The core of the manufacturing process relied on a custom-built 1m³ 3D printer operating 24/7, requiring operator intervention only every 7 to 9 hours for filament reloads or part removal.

To handle the structural integrity of these giant prints without excessive weight, we utilized a **0.8mm nozzle** and configured Cura to generate **internal tree-like circular columns (2-3mm thick)**. This provided massive reinforcement to critical structural points, largely eliminating the need for external support structures.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/sculpture-production/printer1m.png" title="Large format 3D Printer" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The custom 1m³ 3D printer capable of producing massive monolithic structures.
</div>

*Below is a video demonstrating the printing process of a giant vase.*

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include video.html path="assets/video/projects/sculpture-production/vase-printing.mp4" class="img-fluid rounded z-depth-1" autoplay=true loop=true muted=true %}
    </div>
</div>

## Post-Processing & Finishing

Once a piece left the print bed, it was transferred to a dedicated post-processing zone separated into three distinct sections: **Polishing, Putty/Fiberglass Reinforcement, and Painting.**

1. **Thermal Smoothing & Sanding:** The piece was initially treated with a heat gun to remove filament stringing. Operators then used vibratory polishers equipped with custom water-misting adapters to drastically reduce airborne dust while achieving a smooth surface finish.
2. **Reinforcement:** Depending on the final use case, pieces were filled with a specialized putty mimicking a clay texture. For items requiring extreme stability, plaster was injected into the base, or a fiberglass and resin shell was applied before a final sanding pass.
3. **Painting & Artistry:** A base primer was applied before airbrush detailing. Because local artistry was a huge marketing point for the workshop, the foundational painting was done in-house, and pieces were sometimes sent to local artisans for specialized finishing touches.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/sculpture-production/vase1.jpeg" title="Raw 3D printed vase" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/sculpture-production/vase3.jpg" title="Sanding and polishing" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/sculpture-production/vase4.jpg" title="Final painted vase" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Progression from raw PLA print (left), through the sanding and putty phase (center), to the finalized airbrushed product (right).
</div>

## Impact & Results

The initial test run of 1-meter tall vases provided all the necessary insights to refine the Standard Operating Procedures (SOPs) for each station.

The primary bottleneck was the massive 3D printer, which could take anywhere from 4 hours to 5 days to complete complex geometries, consuming up to 3 kilograms of material a day. To optimize this, we distributed the workload: accessories and extensions were printed on smaller 50x50x50cm machines, reserving the 1m³ printer exclusively for the main structural bodies.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/sculpture-production/mesa1.jpg" title="Workshop table" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/sculpture-production/mesa2.jpg" title="Workshop setup" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The organized post-processing workshop stations.
</div>

**Key Achievements:**
* **Lead Time Reduction:** Delivery times per project plummeted from 1-2 months down to just **1 to 3 weeks**.
* **Cost Efficiency:** By implementing a cost calculation matrix for each work order and optimizing sanding/painting tools, overhead costs were minimized.
* **Operational Independence:** After delivering the machines, establishing the workflow, creating SOPs, and running the first 3 major work orders (producing over 20 large sculptures), the management of the factory line was successfully handed over to the workshop owner in 2022.

<div class="row justify-content-sm-center">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/sculpture-production/vase2.jpg" title="First large format print" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Holding the very first piece produced on the large-format 3D printer.
</div>
