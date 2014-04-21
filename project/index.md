---
layout: home
---

<div class="index-content project">
    <div class="section">
        <ul class="artical-cate">
            <li><a href="/"><span>Notes</span></a></li>
            <li class="on"><a href="/project"><span>Project</span></a></li>
	    <li><a href="/vfx"><span>VFX</span></a></li>
	    <li><a href="/aboutme"><span>About Me</span></a></li>
            <li><a href="/opinion"><span>方块字</span></a></li>
        </ul>

        <div class="cate-bar"><span id="cateBar"></span></div>

        <ul class="artical-list">
        {% for post in site.categories.project %}
            <li>
                <h2>
                    <a href="{{ post.url }}">{{ post.title }}</a>
                </h2>
            </li>
        {% endfor %}
        </ul>
    </div>
    <div class="aside">
    </div>
</div>
