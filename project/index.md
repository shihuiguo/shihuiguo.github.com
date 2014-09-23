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
	<div class="divider"></div>
        <ul class="artical-list">
        {% for post in site.categories.project %}
            <li>
		<div class = "featureimage" >
			<img style="width:160px;" src="../images/{{ post.featureimage }}" /> 
		</div>
		<div class = "featuretext">
		        <div class="title">
			   	<h2>{{ post.title }}</h2>
			</div>
			<div class="moreinfo">
				<p>
					{{ post.author }}, {{ post.venue }} {{ post.year }}
					<a href="{{ post.paperlink }}"> [Paper] </a>
					<a href="{{ post.demolink }}"> [Demo] </a>
				</p>
			</div>
		</div>		
            </li>
        {% endfor %}
        </ul>
    </div>
</div>
