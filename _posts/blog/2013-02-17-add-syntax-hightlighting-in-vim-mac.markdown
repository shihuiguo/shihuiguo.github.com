---
layout: post
status: publish
published: true
title: Add Syntax Hightlighting & Set Indent Size in Vim (Mac)
author: Shihui Guo
author_login: yierbosimao
author_email: mr.shihuiguo@gmail.com
wordpress_id: 130
wordpress_url: http://www.guoshihui.net/?p=130
date: '2013-02-17 12:13:12 +0800'
date_gmt: '2013-02-17 12:13:12 +0800'
categories:
- blog
- linux
tags: []
comments: []
---
<p>Just tell Vim to first recognize the filetype which its opening and perform the syntax highlighting.</p>
<p>Open the vim configuration file<br />
<code><br />
vi ~/.vimrc<br />
</code><br />
Create a new file ".vimrc" if this doesn't exist. And add the following lines to the file:<br />
<code><br />
filetype on<br />
syntax on<br />
set smartindent<br />
set tabstop=4<br />
set shiftwidth=4<br />
set expandtab<br />
</code><br />
Then save and quit, restart your vim, it should be working now.</p>
<p>The same should be working in linux as well.</p>
