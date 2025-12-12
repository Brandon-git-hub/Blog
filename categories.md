---
layout: page
title: "Categories"
permalink: /categories/
---

{% assign posts = site.posts %}

# 🗂️ Categories

<!-- ===============================
     Category Index (Card / Chip style)
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

{% assign icon_map =
  "Travel:🏞️,Sea:🌊,Hiking:🥾,Cafe:☕,City:🏙️,Photography:📸,Life:🧳"
  | split: ","
%}

<ul class="cat-index">
{% for c in uniq_cats %}

  {% assign icon = "📁" %}
  {% for pair in icon_map %}
    {% assign kv = pair | split: ":" %}
    {% if kv[0] == c %}
      {% assign icon = kv[1] %}
    {% endif %}
  {% endfor %}

  <li class="cat-chip">
    <a href="#{{ c | slugify }}">
      <span class="cat-emoji" aria-hidden="true">{{ icon }}</span>
      <span class="cat-name">{{ c }}</span>
    </a>
  </li>

{% endfor %}
</ul>

---

<!-- ===============================
     Category Sections
     =============================== -->

{% for c in uniq_cats %}

  {% assign icon = "📁" %}
  {% for pair in icon_map %}
    {% assign kv = pair | split: ":" %}
    {% if kv[0] == c %}
      {% assign icon = kv[1] %}
    {% endif %}
  {% endfor %}

## {{ icon }} {{ c }}

<ul class="cat-post-list">
{% for p in posts %}
  {% if p.categories and p.categories contains c %}
    <li>
      📌 <a href="{{ p.url | relative_url }}">{{ p.title }}</a>
      <span class="post-date">({{ p.date | date: "%Y-%m-%d" }})</span>
    </li>
  {% endif %}
{% endfor %}
</ul>

{% endfor %}
