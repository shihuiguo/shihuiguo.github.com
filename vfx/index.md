---
layout: home
---

<div class="index-content vfx">
    <div class="section">
        <ul class="artical-cate">
            <li><a href="/"><span>Notes</span></a></li>
            <li ><a href="/project"><span>Project</span></a></li>
            <li class="on"><a href="/vfx"><span>VFX</span></a></li>
	    <li><a href="/aboutme"><span>About Me</span></a></li>
            <li><a href="/opinion"><span>方块字</span></a></li>
        </ul>
	<div class="divider"></div>
        <ul class="artical-list">
        {% for post in site.categories.vfx%}
            <li>
                <h2>
                    <a href="{{ post.url }}">{{ post.title }}</a>
                </h2>
            </li>
        {% endfor %}
        </ul>
    </div>
</div>
