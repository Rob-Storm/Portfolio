---
layout: default
title: Projects
---
<h1>Projects</h1>
<ul>
  {% for project in site.projects %}
    <li>
      <a href="{{ relative_url | project.url }}">{{ project.title }}</a>
      – {{ project.description }}
    </li>
  {% endfor %}
</ul>
