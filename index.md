---
layout: page
title: "Brandon's Blog"
---

Welcome to my blog！  
I will update my life experience here.

## 📚 Recent Posts

{% for p in site.posts limit:10 %}
- 📌 [{{ p.title }}]({{ p.url | relative_url }})  
  <small>Category: <code>{% if p.categories %}{{ p.categories | join: ', ' }}{% else %}Uncategorized{% endif %}</code></small>
{% endfor %}

[Browse by category →]({{ '/categories/' | relative_url }})
