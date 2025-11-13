---
layout: default
title: Articles
---
<h1>Articles</h1>
<ul>
  {% for article in site.articles %}
    <li>
      <a href="{{ article.url | relative_url }}">{{ article.title }}</a>
      – {{ article.description }}
    </li>
  {% endfor %}
</ul>
