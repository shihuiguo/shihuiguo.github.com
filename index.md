---
layout: default
---
<div class="index-content home">
    <div class="section">
        {% include menubar.html %}
	
	<div class="divider"></div>
	<div class="bio">
	<h3><a name="project" class="anchor" href="#project"><span class="octicon octicon-link"></span></a>Short Bio</h3>
	<p>I am currently a research-track assistant professor in School of Software, Xiamen University. I obtained my bachelor from Yuanpei College, Peking University (2010), China and Ph.D. from National Centre for Computer Animation, Bournemouth University, UK (2015). My Ph.D. supervisors are <a href="http://nccastaff.bournemouth.ac.uk/jzhang/">Prof. Jianjun Zhang</a> and <a href="http://staffprofiles.bournemouth.ac.uk/display/jchang">Assoc Prof. Jian Chang</a>. During my Ph.D, I also visited <a href="http://people.ucas.ac.cn/~wangwencheng">Prof. Wencheng Wang</a> from State Key Laboratory of Computer Science in Institute of Software, Chinese Academy of Science. After that I joined Institute of Media Innovation in Nanyang Technological University, under the supervision of <a href="http://nadiathalmann.com/index.html">Prof. Nadia Thalmann</a>, before moving back to China</p>
	</div>

	<div class="fullsection">
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
