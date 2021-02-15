---
layout: page
title: "Algorithm"
permalink: /posts/
main_nav: true
---

{% for post in site.categories["Algorithm"] %}
  <h2>
    <a href="{{ post.url | prepend: site.baseurl }}" style="color:black">{{ post.title }}</a>
  </h2>
  <span class="post-date">- {{ post.date | date_to_long_string }}</span>
  {% if forloop.last == false %}<hr>{% endif %}
{% endfor %}

<!--
{% for category in site.categories %}
  {% capture cat %}{{ category | first }}{% endcapture %}
  <h2 id="{{cat}}">{{ cat | capitalize }}</h2>
  {% for desc in site.descriptions %}
  <p class="desc"><em>{{ desc.desc }}</em></p>
  {% if desc.cat == cat %}
    <p class="desc"><em>{{ desc.desc }}</em></p>
  {% endif %}
  {% endfor %}
  <ul class="posts-list">
  {% for post in site.categories[cat] %}
    <li>
      <strong>
        <a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
      </strong>
      <span class="post-date">- {{ post.date | date_to_long_string }}</span>
    </li>
  {% endfor %}
  </ul>
  {% if forloop.last == false %}<hr>{% endif %}
{% endfor %}
<br> -->