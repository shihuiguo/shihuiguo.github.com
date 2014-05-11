---
layout: post
status: publish
published: true
title: Using base64 to decode/encode a string using Linux Command Line
author: Shihui Guo
author_login: yierbosimao
author_email: mr.shihuiguo@gmail.com
wordpress_id: 144
wordpress_url: http://www.guoshihui.net/?p=144
date: '2012-12-18 12:04:03 +0800'
date_gmt: '2012-12-18 12:04:03 +0800'
categories:
- blog
- linux
tags: []
comments: []
---
<p>Personally I think it's a good way to prevent some email spammer to get your email address.</p>
<p>So to encode your email,<br />
<code><br />
$ echo "youremail@domain.com" | base64<br />
</code><br />
It will return the encoded string:<br />
<code><br />
eW91cmVtYWlsQGRvbWFpbi5jb20K<br />
</code><br />
To decode, do:<br />
<code><br />
echo "eW91cmVtYWlsQGRvbWFpbi5jb20K" | base64 -d<br />
</code><br />
It will return exactly your information.</p>
<p>Hope it helps!</p>
