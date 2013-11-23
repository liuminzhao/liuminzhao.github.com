---
layout: default
title: Minzhao Liu
---
{% include JB/setup %}

I blogged my notes here in case I forget about them. I am so forgetful and always broke my laptops.

<ul class="posts">
{% for post in site.posts limit:5 %}
<li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}
</ul>
