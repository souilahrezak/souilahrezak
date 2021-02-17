---
layout: page
title: التصنيفات
permalink: /categories/
sitemap: false
---
<div class="categories">
    <a name="top"></a>
    <ul>
    {% assign categories = site.categories | sort %}
    {% for category in categories %}
    <li>
        <a href="#{{ category | first | slugify }}">{{ category[0] | replace:'-', ' ' }} <span>{{ category | last | size }}</span></a>
    </li>
    {% endfor %}
    </ul>
</div>


<div id="blog-index">
    {% for category in categories %}
        <h3 class="archivetitle">
            <a name="{{ category[0] }}"></a>
            {{ category[0] | replace:'-', ' ' }}
            <i class="badge">({{ category | last | size }})</i>
        </h3>
        <ul class="side-nav">
            {% assign sorted_posts = site.posts | sort: 'title' %}
            {% for post in sorted_posts %}
                {%if post.categories contains category[0]%}
                    <li>
                    <a href="{{ site.baseurl }}{{ post.url }}">{{post.title}}</a>
                    <span id="data-category"> {{ post.date |  date: "%m/%d/%y" }} </span>
                    </li>
                {%endif%}
            {% endfor %}
        <a href="/categories/#top" class="top">
            <small>العودة إلى أعلى الصفحة</small>
          </a>
        </ul>
    {% endfor %}
</div>
