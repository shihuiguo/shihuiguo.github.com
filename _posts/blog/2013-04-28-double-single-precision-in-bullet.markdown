---
layout: post
status: publish
published: true
title: Double & Single Precision in Bullet
author: Shihui Guo
author_login: yierbosimao
author_email: mr.shihuiguo@gmail.com
excerpt: "Numeric Stability is an annoying problem when we write algorithms, so here
  Bullet addresses this problem by defining a general type: btScalar, which can be
  either float or double. Therefore, it provides two ways for compiling, one is single
  precision (float), the other is double precision (double).\r\n\r\nObviously double
  precision is able to reduce the numeric error, thus improving the stability. From
  my experience, the speed performance is not significantly affected (simple scene
  tested).\r\n"
wordpress_id: 527
wordpress_url: http://www.guoshihui.net/?p=527
date: '2013-04-28 17:13:08 +0800'
date_gmt: '2013-04-28 17:13:08 +0800'
categories: [blog, bullet]
---
<p>Numeric Stability is an annoying problem when we write algorithms, so here Bullet addresses this problem by defining a general type: btScalar, which can be either float or double. Therefore, it provides two ways for compiling, one is single precision (float), the other is double precision (double).</p>
<p>Obviously double precision is able to reduce the numeric error, thus improving the stability. From my experience, the speed performance is not significantly affected (simple scene tested).<br />
<a id="more"></a><a id="more-527"></a><br />
To utilize the double precision, you need to first compile the libraries in double precision mode. Bullet uses cmake when compiling the libraries, turn on the option <em>USE_DOUBLE_PRECISION</em> by either using cmake gui, or editing CMakeList.txt directly<br />
<code><br />
OPTION(USE_DOUBLE_PRECISION "Use double precision"      OFF)<br />
</code><br />
You may need to remove the CMakeCache.txt to make a successful recompilation.</p>
<p>To compile and link with doulbe-precision libraries, we use codeblocks to build different targets, one is single precision, the other is double precision. </p>
<p>First, add BT_USE_DOUBLE_PRECISION to the #defines option in build target<br />
<a href="http://www.guoshihui.net/wp-content/uploads/2013/04/Screenshot-from-2013-04-28-180510.png"><img src="http://www.guoshihui.net/wp-content/uploads/2013/04/Screenshot-from-2013-04-28-180510-300x247.png" alt="Screenshot from 2013-04-28 18:05:10" width="300" height="247" class="alignnone size-medium wp-image-531" /></a></p>
<p>Second, change the compile and link paths to respective places. Remember that you got two different sets of libraries now.</p>
<p>Then you should see the differences. Go into the debug mode, check one variable, in single precision mode, it is normally 1e-10, but in double precision mode, it can be 1e-20, which makes huge differences.</p>
<p>A simple demo may also clarify the differences. Two videos are captured after two minutes simulation, the leg should swing back and forth in a single plane.</p>
<p><strong>Single Precision</strong><br />
http://www.youtube.com/watch?v=EfgsvjDJFB0</p>
<p><strong>Double Precision</strong><br />
http://www.youtube.com/watch?v=ndm_q8ck5-o</p>
