---
layout: template
---

<div class="row">
    {% for article in site.article %}      
      <div class="col-12 mb-5">
          <a href="{{ article.url }}" style="text-decoration: none; color: #34383c">
              <div class="col-12">
                  <h1>{{ article.title }}</h1>
              </div>
              <div class="col-12">
                  <p>{{ article.sub_title }}</p>
              </div>
              <div class="col-12 text-right mb-2">
                  <small>{{ article.created_date }}</small>
              </div>
          </a>
      </div>
    {% endfor %}
</div>