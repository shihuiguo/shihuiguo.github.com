---
layout: post
status: publish
published: true
title: linux .la/.lo/.o file
author: Shihui Guo
author_login: yierbosimao
author_email: mr.shihuiguo@gmail.com
wordpress_id: 423
wordpress_url: http://www.guoshihui.net/?p=423
date: '2013-03-16 23:10:25 +0800'
date_gmt: '2013-03-16 23:10:25 +0800'
categories:
- blog
- linux
tags: []
comments: []
---
<p>.lo file is a library object, which may be built into a shared library</p>
<p>.la file is a text-based file created by libtool, that includes description of library and enables to create platform independent libraries. For example, in Linux, the library files are .a/.so, in Windows, they could be .a/.dll. Libtool keeps a list of names of .lo files which is used to create the library in .la file.   </p>
<p>.o file is a standard object file</p>
