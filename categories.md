---
layout: page
title: Categories
permalink: /categories/
sitemap: false
---

<div>
    {% assign categories = site.categories | sort %}
    <ul class="columns">
    {% for category in categories %}
        <li>
            <a href="#{{ category | first | slugify }}">
                    <code>{{ category[0] | replace:'-', ' ' }}</code> ({{ category | last | size }})
            </a>
        </li>
    {% endfor %}
    </ul>
</div>

<div id="index">
    {% for category in categories %}
        <a name="{{ category[0] }}"></a>
        <h2>{{ category[0] | replace:'-', ' ' }} ({{ category | last | size }})</h2>
        {% assign sorted_posts = site.posts | sort: 'date' | reverse %}
        {% for post in sorted_posts %}
            {%if post.categories contains category[0]%}
                <li>
                      {%- assign date_format = "%Y-%m-%d" -%}
                        [ {{ post.date | date: date_format }} ] <a href="{{ post.url | relative_url }}">{{ post.title | escape }}</a>
                </li>
            {%endif%}
        {% endfor %}
    {% endfor %}
</div>