---
layout: page
title: "Home Page"
---

Welcome to my blog！  
I will update my life experience here.

## 📚 Recent Posts

{% assign icon_map =
  "Travel:🏞️,Sea:🌊,Hiking:🥾,Cafe:☕,City:🏙️,Photography:📸,Life:🧳"
  | split: ","
%}

<ul class="post-list">
{% assign posts = site.posts | sort: "date" | reverse %}
{% for p in posts limit:10 %}

  {% assign icon = "📁" %}
  {% if p.categories %}
    {% assign c = p.categories[0] %}
    {% for pair in icon_map %}
      {% assign kv = pair | split: ":" %}
      {% if kv[0] == c %}
        {% assign icon = kv[1] %}
      {% endif %}
    {% endfor %}
  {% endif %}

  <li>
    <span class="post-icon" aria-hidden="true">{{ icon }}</span>
    <a href="{{ p.url | relative_url }}">{{ p.title }}</a>
    {% if p.categories %}
      <span class="post-cat">{{ p.categories | join: ", " }}</span>
    {% endif %}
  </li>

{% endfor %}
</ul>

<p style="margin-top:1.2rem;">
  👉 <a href="{{ '/categories/' | relative_url }}">Browse by category</a>
</p>
