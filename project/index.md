---
layout: default
title: Proejct
search_omit: true
---

<ul class="post-list">
{% for post in site.categories.project %} 
  <li><article><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }} <span class="entry-date"><time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%B %d, %Y" }}</time></span>{% if post.excerpt %} <span class="excerpt">{{ post.excerpt }}</span>{% endif %}</a></article></li>
{% endfor %}
</ul>