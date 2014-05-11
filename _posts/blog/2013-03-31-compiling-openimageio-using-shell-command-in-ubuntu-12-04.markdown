---
layout: post
status: publish
published: true
title: Compiling OpenImageIO using Shell Command in Ubuntu 12.04
author: Shihui Guo
author_login: yierbosimao
author_email: mr.shihuiguo@gmail.com
wordpress_id: 463
wordpress_url: http://www.guoshihui.net/?p=463
date: '2013-03-31 12:13:15 +0800'
date_gmt: '2013-03-31 12:13:15 +0800'
categories:
- blog
- linux
- cg
tags: []
comments: []
---
<p>Basically the main procedure is posted on the openimageio wiki page, see reference below. However I encounter the following error:</p>
<pre>
<em>libOpenImageIO.a(tbb_misc.cpp.o): In function `__TBB_machine_store8_slow_perf_warning':
tbb_misc.cpp:(.text+0x342): undefined reference to `tbb::internal::runtime_warning(char const*, ...)'</em>
</pre>
<p>After looking through the source code, this function is defined in /src/include/tbb/tbb_assert_impl.h, not in tbb_misc.h. So we simply include the header file in tbb_misc.cpp, that's done!<br />
<code><br />
// In tbb_misc.cpp file, Add this following line at the beginning<br />
#include "tbb/tbb_assert_impl.h"<br />
</code></p>
<p>References:<br />
<a href="https://sites.google.com/site/openimageio/checking-out-and-building-openimageio" >OpenImageIO Wiki</a></p>
