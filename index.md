---
layout: template
---

{% for post in site.posts %}      
  <div class="mb-5">
      <a href="{{ post.url }}" style="text-decoration: none; color: #34383c">
          <h1>{{ post.title }}</h1>
          <p style="text-align: center">{{ post.sub_title }}</p>
          <div class="text-right">
              <small class="text-right">{{ post.date | date_to_string }}</small>
          </div>
      </a>
  </div>
{% endfor %}