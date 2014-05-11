---
layout: post
status: publish
published: true
title: Matlab ODE function with changing arguments
author: Shihui Guo
author_login: yierbosimao
author_email: mr.shihuiguo@gmail.com
wordpress_id: 628
wordpress_url: http://www.guoshihui.net/?p=628
date: '2013-08-22 12:44:30 +0800'
date_gmt: '2013-08-22 12:44:30 +0800'
categories:
- blog
- Matlab
tags: []
comments: []
---
<p>The main point is to differentiate between arguments and parameters. Arguments can change during the ODE integration steps, but parameters cannot. See this simple  example:</p>
<pre><code>
clear;
param = struct('beta', 1000);
[T,Y] = ode45(@(t, y)odeFun(t, y, param),[0 3],[2 0]);
function dy = odeFun(t, y, param)
if t > 1
	param.beta = 50;
end
dy = zeros(2,1);    % a column vector
dy(1) = y(2);
dy(2) = -param.beta*y(1);
</code></pre>
