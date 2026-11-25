---
layout: page
title: Projects
permalink: /projects/
description: Engineering case studies across automation, plant reliability, embedded IoT, software utilities, and product design.
nav: true
nav_order: 3
published: true
---

<!-- pages/projects.md -->
<style>
  .project-filters {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    margin: 0 0 24px 0;
  }
  .project-filter-btn {
    background: var(--global-card-bg-color);
    color: var(--global-text-color);
    border: 1px solid var(--global-divider-color);
    border-radius: 999px;
    padding: 6px 14px;
    font-size: 0.85rem;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.18s ease;
  }
  .project-filter-btn:hover,
  .project-filter-btn.active {
    background: var(--global-theme-color);
    color: #ffffff;
    border-color: var(--global-theme-color);
  }
  .projects-unified-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(265px, 1fr));
    gap: 22px;
    align-items: stretch;
  }
  .project-card-wrapper {
    display: flex;
  }
  .project-card-wrapper.is-hidden {
    display: none;
  }
  .project-card-link {
    display: flex;
    width: 100%;
    text-decoration: none !important;
    color: inherit !important;
  }
  .project-modern-card {
    display: flex;
    flex-direction: column;
    width: 100%;
    background: var(--global-card-bg-color);
    border: 1px solid var(--global-divider-color);
    border-radius: 12px;
    overflow: hidden;
    transition: transform 0.18s ease, box-shadow 0.18s ease, border-color 0.18s ease;
  }
  .project-modern-card:hover {
    transform: translateY(-4px);
    border-color: var(--global-theme-color);
    box-shadow: 0 10px 24px rgba(0, 0, 0, 0.18);
  }
  .project-card-media {
    width: 100%;
    aspect-ratio: 16 / 10;
    overflow: hidden;
    background: #161b22;
    border-bottom: 1px solid var(--global-divider-color);
  }
  .project-card-media figure,
  .project-card-media picture {
    display: block;
    width: 100%;
    height: 100%;
    margin: 0 !important;
  }
  .project-card-media img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    display: block;
  }
  .project-card-content {
    display: flex;
    flex-direction: column;
    flex: 1;
    padding: 16px 18px 14px;
  }
  .project-card-title {
    font-size: 1.06rem;
    font-weight: 700;
    line-height: 1.3;
    margin: 0 0 8px 0;
    color: var(--global-text-color);
  }
  .project-card-hook {
    font-size: 0.88rem;
    line-height: 1.48;
    color: var(--global-text-color-light);
    margin: 0 0 14px 0;
    flex: 1;
  }
  .project-card-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
    padding-top: 10px;
    border-top: 1px solid var(--global-divider-color);
  }
  .project-tag-pill {
    font-size: 0.72rem;
    font-weight: 600;
    padding: 3px 9px;
    border-radius: 999px;
    background: rgba(128, 128, 128, 0.14);
    color: var(--global-text-color);
    letter-spacing: 0.2px;
  }
  .project-tag-pill.is-primary {
    background: var(--global-theme-color);
    color: #ffffff;
  }
</style>

{%- assign sorted_projects = site.projects | where_exp: "p", "p.published != false" | sort: "date" | reverse -%}

<div class="projects">
  <div class="project-filters" id="project-filters" role="group" aria-label="Filter projects by category">
    <button type="button" class="project-filter-btn active" data-filter="all">All ({{ sorted_projects.size }})</button>
    {%- assign all_cats = sorted_projects | map: "category" | uniq -%}
    {%- for cat in all_cats -%}
      {%- if cat and cat != "" -%}
      <button type="button" class="project-filter-btn" data-filter="{{ cat | slugify }}">{{ cat }}</button>
      {%- endif -%}
    {%- endfor -%}
  </div>

  <div class="projects-unified-grid" id="projects-grid">
    {%- for project in sorted_projects -%}
      {% include projects.html %}
    {%- endfor -%}
  </div>
</div>

<script>
  document.addEventListener("DOMContentLoaded", function () {
    const buttons = document.querySelectorAll(".project-filter-btn");
    const cards = document.querySelectorAll(".project-card-wrapper");
    buttons.forEach(function (btn) {
      btn.addEventListener("click", function () {
        const filter = btn.getAttribute("data-filter");
        buttons.forEach(function (b) { b.classList.remove("active"); });
        btn.classList.add("active");
        cards.forEach(function (card) {
          const cat = card.getAttribute("data-category");
          if (filter === "all" || cat === filter) {
            card.classList.remove("is-hidden");
          } else {
            card.classList.add("is-hidden");
          }
        });
      });
    });
  });
</script>
