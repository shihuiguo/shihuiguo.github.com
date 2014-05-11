---
layout: post
status: publish
published: true
title: CJK+GBK+Hyperref+pdflatex 目录/书签乱码解决办法
author: Shihui Guo
author_login: yierbosimao
author_email: mr.shihuiguo@gmail.com
excerpt: "由于环境配置限制的比较死，就是CJK包下，用的是GBK的编码，还需要要hyperref来做超链接，用的是pdflatex编译，尝试了若干种办法之后，发现下面的方法适合我的问题，故分享之。看网上的其他的一些配置环境，可以有更简单的方法，例如用xelatex，CJKutf8等等，对于我这种懒人，就先继续在这个环境下工作吧。\r\n\r\n方法的核心就是用gbk2uni这个小工具把.out目录文件由gbk转换为unicode，然后再重新生成目录，步骤如下：\r\n"
wordpress_id: 244
wordpress_url: http://www.guoshihui.net/?p=244
date: '2013-03-02 23:27:16 +0800'
date_gmt: '2013-03-02 23:27:16 +0800'
categories:
- blog
- latex
tags: []
comments: []
---
<p>由于环境配置限制的比较死，就是CJK包下，用的是GBK的编码，还需要要hyperref来做超链接，用的是pdflatex编译，尝试了若干种办法之后，发现下面的方法适合我的问题，故分享之。看网上的其他的一些配置环境，可以有更简单的方法，例如用xelatex，CJKutf8等等，对于我这种懒人，就先继续在这个环境下工作吧。</p>
<p>方法的核心就是用gbk2uni这个小工具把.out目录文件由gbk转换为unicode，然后再重新生成目录，步骤如下：<br />
<a id="more"></a><a id="more-244"></a><br />
- pdflatex source.tex, 生成source.out<br />
- ./gbk2uni -l source.out, -l选项可以避免转换后的.out被覆盖，否则的话还是会有乱码。<br />
- pdflatex source.tex， 重新生成文档  </p>
<p>gbk2uni没有现成的程序，需要从ctex网站下载源代码，然后自己编译，其实就是两个文件，我在这里也给出copy，为我自己以后留个备份：<br />
<a href="http://www.guoshihui.net/wp-content/uploads/2013/03/gbk2uni.c">gbk2uni.c</a><br />
<a href="http://www.guoshihui.net/wp-content/uploads/2013/03/gbk2uni.h">gbk2uni.h</a></p>
<p>编译：<br />
<code><br />
g++ -o gbk2uni gbk2uni.c<br />
</code></p>
<p>Hyperref的包里最好加上CJKbookmark选项<br />
<code><br />
\useackage[CJKbookmarks=true]{hyperref}<br />
</code></p>
