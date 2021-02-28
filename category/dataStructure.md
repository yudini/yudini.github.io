---
layout: page
title: Data Structure
permalink: /Study/datastructure/
main_nav: true
---

<div class="wrapper">
  <div class="wrapper">
    {% for post in site.categories["DataStructure"]  %}
     
      {% capture this_year %}{{ post.date | date: "%Y" }}{% endcapture %}
      {% capture next_year %}{{ post.previous.date | date: "%Y" }}{% endcapture %}

      {% if forloop.first %}
      <h1 id="{{ this_year }}-ref">{{this_year}}</h1>
      <ul class="post-list">
      {% endif %}

      <li>
        <h4>
        <a class="post-list" href="{{ site.baseurl }}{{ post.url }}">
          {{ post.title }} </a> 
          <small> &nbsp;&nbsp;&nbsp;-{{ post.date | date_to_string }}</small>
        </h4>
      </li>

      {% if forloop.last %}
      </ul>
      {% else %}
          {% if this_year != next_year %}
          <ul>
          <h2 id="{{ next_year }}-ref">{{next_year}}</h2>
          </ul>
          {% endif %}
      {% endif %}

    {% endfor %}
    
  </div>
</div> 