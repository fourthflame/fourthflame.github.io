---
layout: default
title: 归档
---

<div class="well article">
{%for post in site.posts %}
    {% unless post.next %}
        <h2>{{ post.date | date: '%Y' }}</h2>
        <ul>
    {% else %}
        {% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}
        {% capture nyear %}{{ post.next.date | date: '%Y' }}{% endcapture %}
        {% if year != nyear %}
            </ul>
            <h2>{{ post.date | date: '%Y' }}</h2>
            <ul>
        {% endif %}
    {% endunless %}
    <li>
        <span class="post-date">
            {% assign date_format = site.date_format.archive %}
            {{ post.date | date: date_format }}
        </span>
            <a href="{{ site.baseurl}}{{ post.url }}">{{ post.title }}</a>
            {% for tag in site.tags %}
                {% for tagpost in tag[1] %}
                    {% if tagpost == post %}
                        <span class="a-light" style="font-size:small;"> &lt;{{ tag[0] }}&gt; </span>
                    {% endif %}
                {% endfor %}
            {% endfor %}
            
            
    </li>
{% endfor %}
</ul>
</div>