---
layout: default
---

{% for post in site.posts %}
  <div class="blog_preview">
    <h2>
      <a href="{{ post.url }}">
        {{ post.title }}
      </a>
    </h2>
    <time datetime="{{ post.date | date: "%Y-%m-%d" }}">{{ post.date | date_to_long_string }}</time>
    {{ post.excerpt }}
    <a class="readMore" href="{{ post.url }}" >Read more...</a>
  </div>
{% endfor %}