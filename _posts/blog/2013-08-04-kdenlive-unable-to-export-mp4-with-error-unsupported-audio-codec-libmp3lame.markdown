---
layout: post
status: publish
published: true
title: 'kdenlive unable to export MP4 with error "Unsupported audio codec: libmp3lame"'
author: Shihui Guo
author_login: yierbosimao
author_email: mr.shihuiguo@gmail.com
wordpress_id: 587
wordpress_url: http://www.guoshihui.net/?p=587
date: '2013-08-04 14:33:32 +0800'
date_gmt: '2013-08-04 14:33:32 +0800'
categories:
- blog
- linux
tags: []
comments:
- id: 82
  author: Maja
  author_email: k.majaa@yahoo.com
  author_url: ''
  date: '2013-09-21 21:57:48 +0800'
  date_gmt: '2013-09-21 21:57:48 +0800'
  content: Thanks a lot! That worked for me.
- id: 83
  author: German
  author_email: iomgoc@gmail.com
  author_url: ''
  date: '2013-12-31 13:35:12 +0800'
  date_gmt: '2013-12-31 13:35:12 +0800'
  content: "Perhaps you will have to do this...\r\n1) Browse to: /home/USERNAME/.kde/share/config\r\n2)
    Delete the file called : kdenliverc"
---
<p>So after upgrading to 12.04 on Ubuntu from 10.04, I cannot export my videos from kdenlive with MPEG-4 option, with the error message "<span style="color: #ff0000;">Unsupported audio codec: libmp3lame</span>"</p>
<p>After installing the lame library with the command:</p>
<pre>

sudo apt-get install libmp3lame0 (the last letter is zero)

</pre>
<p>The issue is still there, so tried another way next</p>
<pre>

sudo apt-get install libavcodec-extra-53

</pre>
<p>Now it works!</p>
