---
layout: page
title: 归档
permalink: /archive/
---

<div class="archive">
{% assign posts_by_year = site.posts | group_by_exp: "post", "post.date | date: '%Y'" %}
{% for year in posts_by_year %}
  <h2 id="{{ year.name }}">{{ year.name }}年</h2>
  <ul class="posts-list">
    {% for post in year.items %}
      <li>
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
        <span class="post-date">{{ post.date | date: "%m-%d" }}</span>
        {% if post.tags %}
          <span class="post-tags">
            {% for tag in post.tags %}
              <a href="/tags/#{{ tag | slugify }}" class="tag-link">{{ tag }}</a>
            {% endfor %}
          </span>
        {% endif %}
      </li>
    {% endfor %}
  </ul>
{% endfor %}
</div>

<style>
.posts-list {
  list-style: none;
  padding-left: 0;
}
.posts-list li {
  margin: 10px 0;
  padding: 10px 0;
  border-bottom: 1px solid #eee;
}
.post-date {
  color: #999;
  font-size: 14px;
  margin-left: 10px;
}
.post-tags {
  margin-left: 15px;
}
.tag-link {
  display: inline-block;
  padding: 2px 8px;
  margin: 0 3px;
  background: #f0f0f0;
  border-radius: 10px;
  font-size: 12px;
  color: #555;
  text-decoration: none;
}
.tag-link:hover {
  background: #007acc;
  color: white;
}
</style>