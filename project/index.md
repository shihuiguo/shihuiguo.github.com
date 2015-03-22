---
layout: home
---

<div class="index-content note">
    <div class="section">
        {% include menubar.html %}
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
					{{ post.author }}, {{ post.venue }} {{ post.year }}, {{ post.note}}
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
