---
layout: page
title: "Categories"
permalink: /categories/
---

{% assign posts = site.posts %}

# 🗂️ Categories

<!-- ===============================
     Category Index
     =============================== -->

{% assign all_cats = "" | split: "" %}
{% for p in posts %}
  {% if p.categories %}
    {% for c in p.categories %}
      {% assign all_cats = all_cats | push: c %}
    {% endfor %}
  {% endif %}
{% endfor %}

{% assign uniq_cats = all_cats | uniq | sort %}

<ul>
{% for c in uniq_cats %}
  <li>📁 <a href="#{{ c | slugify }}">{{ c }}</a></li>
{% endfor %}
</ul>

---

<!-- ===============================
     Category Sections
     =============================== -->

{% for c in uniq_cats %}

## {{ c }}

<ul>
{% for p in posts %}
  {% if p.categories and p.categories contains c %}
    <li>
      📌 <a href="{{ p.url | relative_url }}">{{ p.title }}</a>
      <span style="color:#888; font-size:0.85em;">
        ({{ p.date | date: "%Y-%m-%d" }})
      </span>
    </li>
  {% endif %}
{% endfor %}
</ul>

{% endfor %}
