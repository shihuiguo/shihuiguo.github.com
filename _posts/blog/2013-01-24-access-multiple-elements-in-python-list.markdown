---
layout: post
status: publish
published: true
title: Access Multiple Elements in Python List
author: Shihui Guo
author_login: yierbosimao
author_email: mr.shihuiguo@gmail.com
wordpress_id: 221
wordpress_url: http://www.guoshihui.net/?p=221
date: '2013-01-24 18:06:25 +0800'
date_gmt: '2013-01-24 18:06:25 +0800'
categories:
- blog
- python
tags: []
comments: []
---
<p>Say you are faced with a list and want to access selected elements inside it, here is the way:<br />
<code><br />
#just put the required indexes in the parathesis at the end<br />
selectedEle = [LIST[i] for i in [2, 4, 5]]<br />
</code></p>
<p>If you want to access the same pattern in a 2D list, then do this<br />
<code><br />
# j is the upper level of the list, just like double-layered for loop<br />
selectedEle = [2DLIST[j][i] for j in [4,5, 7] for i in [2, 4, 5]]<br />
</code><br />
But the previous code returns all the elements in a single list, if you want to maintain the original two-layered list, do this<br />
<code><br />
# Please note now, the iterator j is put at the end of the command<br />
selectedEle = [[2DLIST[j][i] for i in [2, 4, 5] for j in [4,5, 7]]]<br />
</code></p>
<p>Python is elegant!</p>
