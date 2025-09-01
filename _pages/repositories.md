---
layout: page
permalink: /repositories/
title: Open-Source Research
description: Welcome to my repositories where I demonstrate my skills in automation, robotics, and full-cycle prototyping—from initial CAD design to final hardware implementation.
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
{% endif %}



---
[link 1]: #  https://github-profile-trophy.vercel.app/
[link 2]: #  https://trophygh.kolioaris.xyz/

{% if site.repo_trophies.enabled %}
<div class="repositories d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
  {% for user in site.data.repositories.github_users %}
    <img src="https://github-profile-trophy.vercel.app/?username={{ user }}&theme={{ site.repo_trophies.theme_dark }}&no-frame=true&no-bg=true&margin-w=15&margin-h=15&column=6" alt="{{ user }}'s GitHub Trophies">
  {% endfor %}
</div>
{% endif %}
  ---


## Highlighted GitHub Repositories

{% if site.data.repositories.github_repos %}
<div class="repositories d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
  {% for repo in site.data.repositories.github_repos %}
    {% include repository/repo.html repository=repo %}
  {% endfor %}
</div>
{% endif %}
