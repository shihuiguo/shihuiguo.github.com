---
layout: home
---

<div class="index-content code">
    <div class="section">
        {% include menubar.html %}
	<div class="divider"></div>
        <ul class="artical-list">
        {% for post in site.categories.code %}
            <li>
                <h2>
                    {{ post.title | truncatewords:10 }}		
                </h2>
		{{ post.authors | truncatewords: 10 }}  <a href="{{ post.githuburl }}">[Github Repository]</a>
            </li>
        {% endfor %}
        </ul>
    </div>
</div>
