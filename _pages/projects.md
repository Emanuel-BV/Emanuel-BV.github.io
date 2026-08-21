---
layout: page
title: Projects
permalink: /projects/
description: A growing collection of projects I worked on.
nav: true
nav_order: 3
display_categories: [Custom Machinery Design, Custom Parts & Products, Software Systems, Engineering Software Utilities, Production Engineering, Analysis & Maintenance Engineering, Machinery Upgrades & Customization]
horizontal: false
published: true
---

<!-- pages/projects.md -->
<div class="projects">
{%- if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {%- for category in page.display_categories %}
  <a id="{{ category | slugify }}"></a>
  <h2 class="category">{{ category }}</h2>
  {%- assign categorized_projects = site.projects | where: "category", category -%}
  {%- assign sorted_projects = categorized_projects | sort: "date" | reverse -%}
  <div class="grid">
    {%- for project in sorted_projects -%}
      {% include projects.html %}
    {%- endfor %}
  </div>
  {%- endfor %}
{%- else -%}
  <!-- Display projects without categories -->
  {%- assign sorted_projects = site.projects | sort: "date" | reverse -%}
  <!-- Generate cards for each project -->
  <div class="grid">
    {%- for project in sorted_projects -%}
      {% include projects.html %}
    {%- endfor %}
  </div>
{%- endif -%}
</div>
