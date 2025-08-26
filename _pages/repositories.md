---
layout: page
permalink: /repositories/
title: Open-Source Research
description: Discover a curated selection of open-source repositories reflecting my contributions to the field of Artificial Intelligence. Explore projects that emphasize collaborative efforts and contribute to the ongoing advancements in this domain.
nav: true
nav_order: 4
---

## GitHub User Statistics

{% if site.data.repositories.github_users %}
<div class="repositories d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
  {% for user in site.data.repositories.github_users %}
    {% include repository/repo_user.html username=user %}
  {% endfor %}
</div>

---

layout: page permalink: /repositories/ title: Repositories description: An overview of my GitHub activity. nav: true nav_order: 4
{% if site.repo_trophies.enabled %}
{% for user in site.data.repositories.github_users %}
{% if site.data.repositories.github_users.size > 1 %}
<h4>{{ user }}</h4>
{% endif %}

<div class="repositories d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
<!-- Light mode trophy -->
<picture>
<source srcset="https://www.google.com/search?q=https://github-profile-trophy.vercel.app/%3Fusername%3D{{ user }}&theme={{ site.repo_trophies.theme_light }}&margin-w=15&margin-h=15&no-bg=true&column=6" media="(prefers-color-scheme: light), (prefers-color-scheme: no-preference)">
<!-- Dark mode trophy -->
<img src="https://www.google.com/search?q=https://github-profile-trophy.vercel.app/%3Fusername%3D{{ user }}&theme={{ site.repo_trophies.theme_dark }}&margin-w=15&margin-h=15&no-bg=true&column=6" alt="{{ user }}'s GitHub Trophies">
</picture>
</div>

{% endfor %}
{% endif %}

<div class="repositories d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
{% for repo in site.data.repositories.github_repos %}
{% include repository/repo_card.html %}
{% endfor %}
</div>

  ---

{% endfor %}
{% endif %}
{% endif %}

## Highlighted GitHub Repositories

{% if site.data.repositories.github_repos %}
<div class="repositories d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
  {% for repo in site.data.repositories.github_repos %}
    {% include repository/repo.html repository=repo %}
  {% endfor %}
</div>
{% endif %}
