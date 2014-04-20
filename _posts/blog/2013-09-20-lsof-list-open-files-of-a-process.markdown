---
layout: post
status: publish
published: true
title: lsof - list open files of a process
author: Shihui Guo
author_login: yierbosimao
author_email: mr.shihuiguo@gmail.com
wordpress_id: 657
wordpress_url: http://www.guoshihui.net/?p=657
date: '2013-09-20 08:29:24 +0800'
date_gmt: '2013-09-20 08:29:24 +0800'
categories:
- Linux OS
tags: []
comments: []
---
<p>This command is really helpful yesterday because when I am running nginx, the access and error log is not written into the files I have specified. Using this command, I found that actually nginx are openning other two log files.</p>
<pre>
sudo lsof -c nginx
</pre>
<p>Reference:<br />
http://forum.nginx.org/read.php?2,58447,58571#msg-58571</p>
