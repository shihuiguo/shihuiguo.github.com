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
                    {{ post.title }}		
                </h2>
		{{ post.authors }}  <a href="{{ post.githuburl }}">[Github Repository]</a>
            </li>
        {% endfor %}
        </ul>
    </div>
</div>
