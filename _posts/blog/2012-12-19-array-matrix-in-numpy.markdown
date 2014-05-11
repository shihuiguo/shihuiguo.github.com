---
layout: post
status: publish
published: true
title: Array & Matrix in numpy
author: Shihui Guo
author_login: yierbosimao
author_email: mr.shihuiguo@gmail.com
wordpress_id: 193
wordpress_url: http://www.guoshihui.net/?p=193
date: '2012-12-19 23:09:41 +0800'
date_gmt: '2012-12-19 23:09:41 +0800'
categories:
- blog
- python
tags: []
comments: []
---
<p>Recently I decide to transfer my code from matlab to python. But compared with matlab, python has far less functions to handle arrays and matrix (perhaps I don't know yet). Some tricky things I discovered:</p>
<p>For array, '*' means element-wise multiplication, and the dot() function is used for matrix multiplication.<br />
For matrix, '*' means matrix multiplication, and the multiply() function is used for element-wise multiplication.</p>
