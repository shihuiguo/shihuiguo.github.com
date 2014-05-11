---
layout: post
status: publish
published: true
title: 'some useful Commands In GCC Compiling under Linux '
author: Shihui Guo
author_login: yierbosimao
author_email: mr.shihuiguo@gmail.com
wordpress_id: 479
wordpress_url: http://www.guoshihui.net/?p=479
date: '2013-04-11 00:06:55 +0800'
date_gmt: '2013-04-11 00:06:55 +0800'
categories:
- blog
- linux
tags: []
comments: []
---
<p><strong>ld --- Listing the gcc library search path</strong></p>
<pre>
ld --verbose | grep SEARCH
</pre>
<p>For example, in my computer, it returns like</p>
<pre>
SEARCH_DIR("/usr/i686-linux-gnu/lib32"); SEARCH_DIR("=/usr/local/lib32"); SEARCH_DIR("=/lib32"); SEARCH_DIR("=/usr/lib32"); SEARCH_DIR("=/usr/local/lib/i386-linux-gnu"); SEARCH_DIR("=/usr/local/lib"); SEARCH_DIR("=/lib/i386-linux-gnu"); SEARCH_DIR("=/lib"); SEARCH_DIR("=/usr/lib/i386-linux-gnu"); SEARCH_DIR("=/usr/lib");
</pre>
<p><strong> ldd --- List the libraries which an executive program needs when running </strong></p>
<pre>
shepherd@shepherd-laptop:~$ ldd /bin/bash 
	linux-gate.so.1 =>  (0x007e9000)
	libtinfo.so.5 => /lib/i386-linux-gnu/libtinfo.so.5 (0x00682000)
	libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0x00110000)
	libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0x00115000)
	/lib/ld-linux.so.2 (0x0075c000)
</pre>
<p><strong>locate --- find a file by filename </strong><br />
locate is a simple command to search file in linux. Use updatedb to update the database which locate uses to search. But don't use updatedb too often because it reads your whole disk...</p>
<pre>
locate somefile

updatedb
</pre>
<p><strong>grep --- find a file by its contents </strong><br />
it's coming coming...</p>
