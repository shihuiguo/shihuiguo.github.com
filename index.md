---
layout: default
---
<div class="index-content home">
    <div class="section">
        {% include menubar.html %}
	
	<div class="divider"></div>
	<div class="bio">
	<h3><a name="project" class="anchor" href="#project"><span class="octicon octicon-link"></span></a>Short Bio</h3>
	<p>I am currently an associate professor in School of Informatics, Xiamen University. I obtained my bachelor from Yuanpei College, Peking University (2010), China and Ph.D. from National Centre for Computer Animation, Bournemouth University, UK (2015). My Ph.D. supervisors are <a href="http://nccastaff.bournemouth.ac.uk/jzhang/">Prof. Jianjun Zhang</a> and <a href="http://staffprofiles.bournemouth.ac.uk/display/jchang">Assoc Prof. Jian Chang</a>. During my Ph.D, I also visited <a href="http://people.ucas.ac.cn/~wangwencheng">Prof. Wencheng Wang</a> from State Key Laboratory of Computer Science in Institute of Software, Chinese Academy of Science. After that I joined Institute of Media Innovation in Nanyang Technological University, under the supervision of <a href="http://nadiathalmann.com/index.html">Prof. Nadia Thalmann</a>, before moving back to China.</p>
	</div>

	<div class="bio separator">
	<h3><a name="project" class="anchor" href="#project"><span class="octicon octicon-link"></span></a>Teaching</h3>
	<ul class="artical-list">
	<li>Dynamic Design and Customized Fabrication of Personalized Robots, July 2017. Part of <a href="http://staff.ustc.edu.cn/~lgliu/Courses/SummerSchool_2017/default.html">USTC Summer School 2017 (中国科技大学《计算机图形学》暑期课程)</a>. This is one of the best summer schools in the fields of computer graphics, <span style="font-weight:bold;">I would encourage undergraduate and graduate students from relevant fields to attend.</span> <a href="https://www.jianguoyun.com/p/DZANRZIQnP3hBRijsDM">[PDF]</a> </li>	
	<li>SOF102 Computer Fundamentals. 2016 Autumn.</li>
	<li>SOF103 C and C++ Programming. 2016 Autumn.</li>
	</ul>
	</div>

	<div class="fullsection">
	<h3><a name="project" class="anchor" href="#project"><span class="octicon octicon-link"></span></a>Selected Publications</h3>
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
						{{ post.author }}, {{ post.venue }}, {{ post.year }}, {{ post.note}}
						<a href="{{ post.paperlink }}"> [Paper] </a>
						<a href="{{ post.demolink }}"> [Demo] </a>
					</p>
				</div>
			</div>		
		    </li>
		{% endfor %}
		</ul>
	</div>
