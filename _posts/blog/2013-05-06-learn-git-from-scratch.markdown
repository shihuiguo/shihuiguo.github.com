---
layout: post
status: publish
published: true
title: Learn Git From Scratch
author: Shihui Guo
author_login: yierbosimao
author_email: mr.shihuiguo@gmail.com
wordpress_id: 546
wordpress_url: http://www.guoshihui.net/?p=546
date: '2013-05-06 21:28:52 +0800'
date_gmt: '2013-05-06 21:28:52 +0800'
categories:
- git
tags: []
comments: []
---
<p>Git is a powerful version control tool, and this is a simple tutorial for you to start using git from scratch.</p>
<p>First, clone an existing project </p>
<pre>
git clone url_to_remote_repository
</pre>
<p>It will build a local copy, which you can start working on.</p>
<p>After you make some changes, do "add" to include all the changes you made to the files</p>
<pre>
git add .
</pre>
<p>Then you commit these changes into local repository:</p>
<pre>
git commit -m "Your Message Here to explain what you have done"
</pre>
<p>The final step is to push your changes to remote repository:</p>
<pre>
git push origin master
</pre>
