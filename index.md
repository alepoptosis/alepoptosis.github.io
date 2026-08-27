---
layout: template
title: alepoptosis
sub_title: Personal Website
---

{% for post in site.posts %}     
<div class="writing-item-bg">
    <a class="writing-item" href="{{ post.url }}">
        <h1>{{ post.title }}</h1>
        <p>{{ post.preview }}</p>
        <div class="writing-meta">
            <div>{{ post.date | date_to_string: "ordinal", "US" }}</div>
            <div>{{ post.category }}</div>
        </div>
    </a>
</div>
{% endfor %}