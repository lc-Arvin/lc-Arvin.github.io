---
layout: page
title: 标签
permalink: /tags/
---

<div class="tags-cloud">
{% assign tags = site.tags | sort %}
{% for tag in tags %}
  <span class="tag-item">
    <a href="#{{ tag[0] | slugify }}" class="tag-link">
      {{ tag[0] }} <span class="tag-count">({{ tag[1].size }})</span>
    </a>
  </span>
{% endfor %}
</div>

<hr>

<div class="tags-list">
{% assign tags = site.tags | sort %}
{% for tag in tags %}
  <h2 id="{{ tag[0] | slugify }}">{{ tag[0] }}</h2>
  <ul class="posts-list">
    {% for post in tag[1] %}
      <li>
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
        <span class="post-date">{{ post.date | date: "%Y-%m-%d" }}</span>
      </li>
    {% endfor %}
  </ul>
{% endfor %}
</div>

<style>
.tags-cloud {
  margin: 20px 0;
  line-height: 2;
}
.tag-item {
  display: inline-block;
  margin: 5px 10px 5px 0;
}
.tag-link {
  padding: 5px 12px;
  background: #f0f0f0;
  border-radius: 15px;
  text-decoration: none;
  color: #333;
  font-size: 14px;
}
.tag-link:hover {
  background: #007acc;
  color: white;
}
.tag-count {
  font-size: 12px;
  color: #666;
}
.posts-list {
  list-style: none;
  padding-left: 0;
}
.posts-list li {
  margin: 8px 0;
  padding-bottom: 8px;
  border-bottom: 1px solid #eee;
}
.post-date {
  color: #999;
  font-size: 14px;
  margin-left: 10px;
}
</style>