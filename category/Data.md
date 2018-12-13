---
layout: page
title: data
---
<div class="tag-list">
  
  {% assign category = page.category | default: page.title %}
  {% for post in site.categories[category] %}
  <div class="tag-group">
        <a href="{{ site.baseurl }}{{ post.url }}">
          {{ post.title }}        </a>
        <small>{{ post.date | date_to_string }}</small>
  </div>
  {% endfor %}
  
</div>