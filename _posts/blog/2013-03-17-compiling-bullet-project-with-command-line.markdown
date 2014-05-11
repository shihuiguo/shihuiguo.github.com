---
layout: post
status: publish
published: true
title: Compiling Bullet project with command line
author: Shihui Guo
author_login: yierbosimao
author_email: mr.shihuiguo@gmail.com
excerpt: "Follow the instructions on Bullet wikipage to compile and install the libraries\r\n<code>\r\n
  mkdir bullet-build\r\n cd bullet-build\r\n cmake ../path/to/bullet -G \"Unix Makefiles\"
  \r\n make -j4\r\n sudo make install\r\n</code>\r\nlibBulletDynamics.a/libBulletCollision.a/libLinearMath.a/libBulletSoftBody
  should be installed in your local library path, which should be /usr/local/lib/\r\n"
wordpress_id: 425
wordpress_url: http://www.guoshihui.net/?p=425
date: '2013-03-17 00:11:50 +0800'
date_gmt: '2013-03-17 00:11:50 +0800'
categories:
- blog
- linux
tags: []
comments: []
---
<p>Follow the instructions on Bullet wikipage to compile and install the libraries<br />
<code><br />
 mkdir bullet-build<br />
 cd bullet-build<br />
 cmake ../path/to/bullet -G "Unix Makefiles"<br />
 make -j4<br />
 sudo make install<br />
</code><br />
libBulletDynamics.a/libBulletCollision.a/libLinearMath.a/libBulletSoftBody should be installed in your local library path, which should be /usr/local/lib/<br />
<a id="more"></a><a id="more-425"></a><br />
The headers, originally in src/, are now installed in local header path, which should be /usr/local/inc/</p>
<p>Choose one demo, and copy the original files (.cpp and .h) to a new dir, and first compile. Here we choose the RagdollDemo:<br />
<code><br />
gcc -I/Path to Bullet/Demos/OpenGL -I/usr/local/include/bullet/ -c main.cpp<br />
gcc -I/Path to Bullet/Demos/OpenGL -I/usr/local/include/bullet/ -c RagdollDemo.cpp<br />
</code></p>
<p>Then link:<br />
<code><br />
gcc main.o RagdollDemo.o -o AppRagdollDemo -lOpenGLSupport -lBulletDynamics -lBulletCollision -lLinearMath -lstdc++ -lglut -lGL -lGLU -L/usr/local/lib/ -L/Path to bullet/Demos/OpenGL/ -L/Path to bullet/Glut (Please notice these two special folder which contain the libraries of glut/GL/GLU)<br />
</code><br />
Then the executable file should be under this dir. Hope this helps.</p>
<p>Note: Bullet provide the Glut/GL/ folder, you may not want to add this to the compile process, because it might lead to conflict with your existing GL files.</p>
<p>The reason I want to do it in command line is that you are forced to specify every parameter, by this way you get a clear idea of what is needed in this process. The best way to learn.</p>
