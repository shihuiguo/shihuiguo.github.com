---
layout: post
status: publish
published: true
title: Bullet CProfileManager Issues
author: Shihui Guo
author_login: yierbosimao
author_email: mr.shihuiguo@gmail.com
wordpress_id: 585
wordpress_url: http://www.guoshihui.net/?p=585
date: '2013-08-01 15:38:49 +0800'
date_gmt: '2013-08-01 15:38:49 +0800'
categories:
- blog
- bullet
tags: []
comments: []
---
<p>The bug messages are just loads of:</p>
<pre>btSimulationIslandManager.cpp:(.text+0x880): undefined reference to `CProfileManager::Start_Profile(char const*)'
btSimulationIslandManager.cpp:(.text+0x1434): undefined reference to `CProfileManager::Stop_Profile()'</pre>
<p>The reason for this is the linking order of bullet libraries, my previous order is "<span style="color: #ff0000;">-lLinearMath</span> -lBulletDynamics -lBulletCollision", but the right order is "-lBulletDynamics -lBulletCollision <span style="color: #ff0000;">-lLinearMath</span>"</p>
<p>Alternatively you can switch the off the profiling by defining -DBT_NO_PROFILE, or edit and enable the line in Bullet/src/LinearMath/btQuickprof.h</p>
<p>References:<br />
http://bulletphysics.org/Bullet/phpBB3/viewtopic.php?f=9&amp;t=2949</p>
