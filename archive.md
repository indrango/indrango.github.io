---
layout: page
title: Archive
---

<ul class="posts">
  {% for post in site.posts %}

    <!-- {% unless post.next %}
      <h3>{{ post.date | date: '%Y' }}</h3>
    {% else %}
      {% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}
      {% capture nyear %}{{ post.next.date | date: '%Y' }}{% endcapture %}
      {% if year != nyear %}
        <h3>{{ post.date | date: '%Y' }}</h3>
      {% endif %}
    {% endunless %} -->

    <li itemscope>
      <h3><a href="{{ site.github.url }}{{ post.url }}">{{ post.title }}</a></h3>
      <p class="post-date"><span><i aria-hidden="true"></i> {{ post.date | date_to_string }} &middot; <i aria-hidden="true"></i> {% include read-time.html %}</span></p>
    </li>

  {% endfor %}
</ul>
