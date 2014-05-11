---
layout: post
status: publish
published: true
title: FFMPEG convert sequences of images into videos
author: Shihui Guo
author_login: yierbosimao
author_email: mr.shihuiguo@gmail.com
wordpress_id: 542
wordpress_url: http://www.guoshihui.net/?p=542
date: '2013-05-04 11:20:08 +0800'
date_gmt: '2013-05-04 11:20:08 +0800'
categories:
- blog
- cg
- ffmpeg
tags: []
comments: []
---
<p>First of all, naming specification for this sequence of image, normally there are two ways, one is with leading zeros, one is without.</p>
<ul>
<ol>Case 1: 1, 2, 3, 4...11, 12, 13, ....100, 111, 112... => %d </ol>
<ol>Case 2: 001, 002, 003, 004, .... 011, 012, 013... 100, ... => %3d </ol>
</ul>
<p>To convert the images without losing quality, there are two options:</p>
<pre>
ffmpeg -i frame%04d.png -vcodec huffyuv test.avi
ffmpeg -i frame%04d.png -vcodec ffv1 -sameq test.avi
</pre>
<p>To control the framerate</p>
<pre>
ffmpeg -r 25 -i frame%04d.png -vcodec huffyuv test.avi
</pre>
<p>Some other alternatives are (not completely lossless, but still get good result):</p>
<pre>
ffmpeg -i frame%04d.png -sameq test.avi (the new version of ffmpeg removed the -sameq option, instead you may need to do -qscale 0)
ffmpeg -i frame%04d.png -vcodec mjpeg -sameq test.avi
</pre>
<p>References:<br />
http://stackoverflow.com/questions/4839303/convert-image-sequence-to-lossless-movie</p>
