---
layout: post
status: publish
published: true
title: Record and Replay Sequence of Commands in Vi
author: Shihui Guo
author_login: yierbosimao
author_email: mr.shihuiguo@gmail.com
wordpress_id: 459
wordpress_url: http://www.guoshihui.net/?p=459
date: '2013-03-30 22:39:34 +0800'
date_gmt: '2013-03-30 22:39:34 +0800'
categories:
- blog
- linux
tags: []
comments: []
---
<p>This is another great advantage which makes me fall in love with vi, just makes your life much simpler.</p>
<p>- Press q to enter the recording mode<br />
- Press any lowcase character, such as "a", as the name of this command sequence. Now it will start recording, as the message (--recording--) appears at the bottom of the screen.<br />
- do any fancy work with vi commands<br />
- Press q to exit and save this sequence of command<br />
- Move cursor to any other proper position to replay command, press @ and the command name ("a", in this example), then miracle happens!</p>
<p>Welcome to the magical world!</p>
