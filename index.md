---
layout: page
title: "Brandon's Blog"
---

Welcome to my blog！  
I will update my life experience here.

## 📚 Recent Posts

{% assign my_pages = site.pages | where_exp: "p", "p.path contains '_posts/'" | where_exp: "p", "p.date != nil" %}

{% assign lines = '' | split: ',' %}
{% for p in my_pages %}
  {% capture date_str %}{{ p.date }}{% endcapture %}
  {% assign date_str = date_str | replace: ' ', '' %}
  {% assign date_arr = date_str | split: ',' %}
  {% assign firstd = date_arr | first %}
  {% assign n = firstd | plus: 0 %}
  {% assign key = n | prepend: '000000' | slice: -6, 6 %}
  {% capture line %}{{ key }}|{{ p.url }}{% endcapture %}
  {% assign lines = lines | push: line %}
{% endfor %}

{% assign sorted_lines = lines | sort | reverse %}

{% capture list_md %}
{% for line in sorted_lines limit:10 %}
  {% assign parts = line | split: '|' %}
  {% assign url = parts[1] %}
  {% assign p = site.pages | where: "url", url | first %}
- 📌 [{{ p.title }}]({{ p.url | relative_url }})  
  <small>Category: <code>{% if p.categories %}{{ p.categories | join: ', ' }}{% else %}Uncategorized{% endif %}</code></small>
{% endfor %}
{% endcapture %}

{{ list_md | markdownify }}

[Browse by category →]({{ '/categories/' | relative_url }})
