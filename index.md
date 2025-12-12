---
layout: page
title: "Brandon's Blog"
---

Welcome to my blog！  
I will update my life experience here.

## 📚 Recent Posts

<ul class="post-list">
{% for p in site.posts limit:10 %}
  <li>
    <a href="{{ p.url | relative_url }}">{{ p.title }}</a>
    <span class="post-cat">{{ p.categories | join: ", " }}</span>
  </li>
{% endfor %}
</ul>

[Browse by category →]({{ '/categories/' | relative_url }})
