
layout: page permalink: /repositories/ title: Repositories description: An overview of my GitHub activity and open-source projects. nav: true nav_order: 4
GitHub Statistics & Trophies
{% if site.repo_trophies.enabled and site.data.repositories.github_users %}

<div class="repositories d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
{% for user in site.data.repositories.github_users %}
<!-- GitHub Trophies -->
<picture>
<source srcset="https://www.google.com/search?q=https://github-profile-trophy.vercel.app/%3Fusername%3D{{ user }}&theme={{ site.repo_trophies.theme_light }}&margin-w=15&margin-h=15&no-bg=true&column=6" media="(prefers-color-scheme: light), (prefers-color-scheme: no-preference)">
<img src="https://www.google.com/search?q=https://github-profile-trophy.vercel.app/%3Fusername%3D{{ user }}&theme={{ site.repo_trophies.theme_dark }}&margin-w=15&margin-h=15&no-bg=true&column=6" alt="{{ user }}'s GitHub Trophies">
</picture>
{% endfor %}
</div>
{% endif %}

Highlighted GitHub Repositories
{% if site.data.repositories.github_repos %}

<div class="repositories d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
{% for repo in site.data.repositories.github_repos %}
{% include repository/repo_card.html %}
{% endfor %}
</div>
{% endif %}
