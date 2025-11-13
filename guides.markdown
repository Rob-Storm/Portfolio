---
layout: default
title: Guides
---
<h1>Guides</h1>
<ul>
  {% for guide in site.guides %}
    <li>
      <a href="{{ guide.url | relative_url }}">{{ guide.title }}</a>
      – {{ guide.description }}
    </li>
  {% endfor %}
</ul>
