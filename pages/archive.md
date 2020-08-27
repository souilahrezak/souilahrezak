---
layout: page
title: الأرشيف
permalink: /archive/
sitemap: false
---
<div id="blog-index">
    {% for post in site.posts %}
      {% unless post.next %}
          <h3 class="archivetitle">
              <a name="{{ post.date | date: '%Y' }}"></a>
              {{ post.date | date: '%Y' }}
          </h3>
      {% else %}
      {% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}
      {% capture nyear %}{{ post.next.date | date: '%Y' }}{% endcapture %}
      {% if year != nyear %}
        <h3 class="archivetitle">
            <a name="{{ post.date | date: '%Y' }}"></a>
            {{ post.date | date: '%Y' }}
        </h3>
      {% endif %}
    {% endunless %}

  <ul class="side-nav">
      <li>
        <a href="{{ site.baseurl }}{{ post.url }}">{{post.title}}</a>
        <span id="data-category"> {{ post.date |  date: "%m/%d/%y" }} </span>
      </li>
  </ul>
  {% endfor %}
</div>
