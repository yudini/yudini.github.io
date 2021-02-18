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
<div class="wrapper">
  <div class="wrapper">
    {% for post in site.posts  %}
     
      {% capture this_year %}{{ post.date | date: "%Y" }}{% endcapture %}
      {% capture next_year %}{{ post.previous.date | date: "%Y" }}{% endcapture %}

      {% if forloop.first %}
      <h1 id="{{ this_year }}-ref">{{this_year}}</h1>
      <ul>
      {% endif %}

      <li>
        <a class="post-list" href="{{ site.baseurl }}{{ post.url }}">
          <h2>{{ post.title }} </h2>
          <small>{{ post.date | date_to_string }}</small>
          // <small>{{ post.date | date: "%Y년 %m월 %d일" }}</small> 
        </a>
      </li>

      {% if forloop.last %}
      </ul>
      {% else %}
          {% if this_year != next_year %}
          </ul>
          <h2 id="{{ next_year }}-ref">{{next_year}}</h2>
          <ul>
          {% endif %}
      {% endif %}

    {% endfor %}
    </ul>
  </div>
</div> 
-->