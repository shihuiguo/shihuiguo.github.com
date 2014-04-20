---
layout: home
---

<div class="index-content project">
    <div class="section">
        <ul class="artical-cate">
            <li><a href="/"><span>Blog</span></a></li>
            <li><a href="/opinion"><span>方块字</span></a></li>
            <li ><a href="/project"><span>Project</span></a></li>
            <li class="on"><a href="/vfx"><span>VFX</span></a></li>
	    <li><a href="/aboutme"><span>About Me</span></a></li>
        </ul>

        <div class="cate-bar"><span id="cateBar"></span></div>

        <ul class="artical-list">
        {% for post in site.categories.vfx%}
            <li>
                <h2>
                    <a href="{{ post.url }}">{{ post.title }}</a>
                </h2>
                <div class="title-desc">{{ post.description }}</div>
            </li>
        {% endfor %}
        </ul>
    </div>
    <div class="aside">
    </div>
</div>
