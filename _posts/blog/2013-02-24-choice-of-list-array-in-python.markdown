---
layout: post
status: publish
published: true
title: Choice of List & Array in Python
author: Shihui Guo
author_login: yierbosimao
author_email: mr.shihuiguo@gmail.com
wordpress_id: 214
wordpress_url: http://www.guoshihui.net/?p=214
date: '2013-02-24 17:01:01 +0800'
date_gmt: '2013-02-24 17:01:01 +0800'
categories:
- blog
- python
tags: []
comments: []
---
<p>list is able to store heterogeneous and arbitrary data, but takes a lot more spaces than C arrays. Array in python is the wrapper of C array structure, which takes up a continuous block of memory and only stores the same type of data.</p>
<p>You should use arrays if you know that everything in the "list" will be of the same type and you want to store the data more compactly. Otherwise, list is more flexible.</p>
<p>Because lists are mutable, when you change that list, all of the references get "automatically" updated. This feature of multiple references to the same list can lead to side effects.</p>
<p>Note that operations that modify the list will modify it in place. This means that if you have multiple variables that point to the same list, all variables will be updated at the same time.<br />
<code><br />
    L = []<br />
    M = L</p>
<p>    # modify both lists<br />
    L.append(obj)<br />
</code><br />
To create a separate list, you can use slicing or the list function to quickly create a copy:<br />
<code><br />
    L = []<br />
    M = L[:] # create a copy</p>
<p>    # modify L only<br />
    L.append(obj)<br />
</code><br />
References:<br />
http://stackoverflow.com/questions/9405322/python-array-v-list<br />
http://effbot.org/zone/python-list.htm</p>
