---
layout: post
status: publish
published: true
title: Using parfor (Matlab) to do parallel computing (CMA-ES Optimization)
author: Shihui Guo
author_login: yierbosimao
author_email: mr.shihuiguo@gmail.com
excerpt: "Recently I am testing CMA-ES optimization to tune the parameters of the
  motion controller for virtual characters, but since the convergence takes such a
  long time, I am thinking to take full advantage of my six core CPU and make things
  faster.\r\n\r\nIn CMA-ES optimization (<a href=\"https://www.lri.fr/~hansen/cmaes_inmatlab.html#matlab\">Matlab
  code</a>), there is an option for enabling the parallel feature:\r\n<code>\r\nopts.EvalParallel
  = 'yes'\r\n</code>\r\n"
wordpress_id: 253
wordpress_url: http://www.guoshihui.net/?p=253
date: '2013-03-06 11:37:19 +0800'
date_gmt: '2013-03-06 11:37:19 +0800'
categories:
- blog
- research
tags: []
comments: []
---
<p>Recently I am testing CMA-ES optimization to tune the parameters of the motion controller for virtual characters, but since the convergence takes such a long time, I am thinking to take full advantage of my six core CPU and make things faster.</p>
<p>In CMA-ES optimization (<a href="https://www.lri.fr/~hansen/cmaes_inmatlab.html#matlab">Matlab code</a>), there is an option for enabling the parallel feature:<br />
<code><br />
opts.EvalParallel = 'yes'<br />
</code><br />
<a id="more"></a><a id="more-253"></a><br />
However, this is just an interface, which passes the whole population into the objective function as a NxM matrix (N is the dimension of freedom, M is the number of population). The output of the objective function should be a 1xM array, which returns the fitness of individual.</p>
<p>To utilize the matlab parfor, there are few things to note:</p>
<ul>
<li>Global variables are not allowed in the code inside the parfor loop</li>
<li>Variables declared outside parfor but used inside parfor, must be properly sliced
</ul>
<p>At last, if you can't make your whole program run in parfor, choose the small heavist-computing part and squeeze it into parfor!</p>
<p>Screenshot of system monitor<br />
<a href="http://www.guoshihui.net/wp-content/uploads/2013/03/Screenshot-2.png"><img src="http://www.guoshihui.net/wp-content/uploads/2013/03/Screenshot-2-300x174.png" alt="Screenshot-2" width="300" height="174" class="alignnone size-medium wp-image-353" /></a></p>
