---
layout: default
title: Blog
permalink: /blog/
---
<div class="blog-page">
  <h1>Blog</h1>
  <p class="page-desc">All posts — math breakdowns, findings, and learning notes.</p>

  <ul class="post-list">
    {% for post in site.posts %}
    <li class="post-list-item">
      <div class="post-list-date">{{ post.date | date: "%B %d, %Y" }}</div>
      <h3 class="post-list-title"><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
      {% if post.excerpt_text %}
      <p class="post-list-excerpt">{{ post.excerpt_text }}</p>
      {% endif %}
    </li>
    {% endfor %}
  </ul>
</div>
