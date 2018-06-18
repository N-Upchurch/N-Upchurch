---
layout: page
title: Categories
permalink: /categories/
activeTab: "categories" 
spielTitle: Pick your poison.
spiel: I try to keep it varied around here.
---

<div id="archives">
{% for category in site.categories %}
    {% assign loopindex = forloop.index | modulo: 2 %}
    {% if loopindex != 0 %}
        <div class="row">
            <div class="archive-group six columns">
                {% capture category_name %}{{ category | first }}{% endcapture %}
                <details>
                    <div id="#{{ category_name | slugize }}"></div>
                    <p></p>
                    <summary>
                        <button>{{ category_name }}</button>
                    </summary>
                    <a name="{{ category_name | slugize }}"></a>
                    {% for post in site.categories[category_name] %}
                    <article class="archive-item">
                        <h4><a href="{{ site.baseurl }}{{ post.url }}">{{post.title}}</a></h4>
                    </article>
                    {% endfor %}
                </details>
            </div>
    {% else %}
        <div class="archive-group six columns">
            {% capture category_name %}{{ category | first }}{% endcapture %}
            <details>
                <div id="#{{ category_name | slugize }}"></div>
                <p></p>
                <summary>
                    <h3 class="category-head">{{ category_name }}</h3>
                </summary>
                <a name="{{ category_name | slugize }}"></a>
                {% for post in site.categories[category_name] %}
                <article class="archive-item">
                    <h4><a href="{{ site.baseurl }}{{ post.url }}">{{post.title}}</a></h4>
                </article>
                {% endfor %}
            </details>
        </div>
    </div>
    {% endif %}
{% endfor %}
</div>