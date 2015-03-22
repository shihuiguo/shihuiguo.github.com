---
layout: home
---

<div class="index-content opinion">
    <div class="section">
        {% include menubar.html %}
	<div class="divider"></div>
        <ul class="artical-list">
        {% for post in site.categories.blog %}
            <li>
                <h2>
                    <a href="{{ post.url }}">{{ post.title }}</a>
                </h2>
            </li>
        {% endfor %}
        </ul>
    </div>
</div>
