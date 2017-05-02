---
layout: default
---
<div class="index-content home">
    <div class="section">
        {% include menubar.html %}
	
	<div class="divider"></div>
	<div class="section">
	<p>I am currently a research-track assistant professor in School of Software, Xiamen University. I obtained my bachelor from Peking University, China and Ph.D. from Bournemouth University, UK. After that I joined Institute of Media Innovation in Nanyang Technological University, under the supervision of Prof. Nadia Thalmann, before moving back to China</p>
	</div>

	<div class="divider"></div>
	<div class="section">
	<h3><a name="project" class="anchor" href="#project"><span class="octicon octicon-link"></span></a>Projects</h3>
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

	<div class="divider"></div>
	<div class="section">
	<h3>
	<a name="education" class="anchor" href="#education"><span class="octicon octicon-link"></span></a>Education</h3>

	<p>2010.10 - 2015.9 Ph.D. Computer Animation. (Supervisor: Prof. Jianjun Zhang & Asso Prof. Jian Chang)</p>
	<p>National Centre for Computer Animation, Bournemouth University</p>

	<p>2006.9 - 2010.7 B.s. Electrical Engineering. (Supervisor: Prof. Xinyu Mao)</p>
	<p>Yuanpei College, Peking University</p>

	<p>2014.3 - 2015.2 State Key Laboratory of Computer Science (Visiting, Supervisor: Prof. Wencheng Wang)</p>
	<p>Institute of Software, Chinese Academy of Sciences</p>
	</div>
