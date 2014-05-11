---
layout: post
status: publish
published: true
title: Building Blender 2.6 on Ubuntu 12.04
author: Shihui Guo
author_login: yierbosimao
author_email: mr.shihuiguo@gmail.com
wordpress_id: 474
wordpress_url: http://www.guoshihui.net/?p=474
date: '2013-04-01 19:32:40 +0800'
date_gmt: '2013-04-01 19:32:40 +0800'
categories:
- blog
- cg
- linux
tags: []
comments: []
---
<h2> Get the source code </h2>
<p><code><br />
cd ~<br />
mkdir blender-svn<br />
cd blender-svn<br />
svn co https://svn.blender.org/svnroot/bf-blender/trunk/blender<br />
</code></p>
<h2> Install dependencies </h2>
<p>I just use the script provided in the source to automatically install the dependencies:<br />
<code><br />
cd ~/blender-svn<br />
./blender/build_files/build_environment/install_deps.sh<br />
</code></p>
<p>However there is an issue with installing OpenImageIO, which I discussed in <a href="http://www.guoshihui.net/2013/03/compiling-openimageio-using-shell-command-in-ubuntu-12-04/">this post</a>. The default folder which this script uses for downloading the OpenImageIO is in ~/src/blender-deps/OpenImageIO-1.1.7. Open the file ~/src/blender-deps/OpenImageIO-1.1.7/src/libutil/tbb_misc.cpp, and add the following line at the beginning:<br />
<code><br />
#include "tbb/tbb_assert_impl.h"<br />
</code><br />
Then rerun the install script again. The script is smart enough to continue where it stops and OpenImageIO should be successfully compiled by now.</p>
<p>What should be noted is that the dependencies installed here should be fed into cmake later, and the detailed message will be given after this script finished and stored in BUILD_NOTES.txt (same folder with the script). The message is like:</p>
<pre>
<code>
If you're using CMake add this to your configuration flags:
  -D BOOST_ROOT=/opt/lib/boost
  -D Boost_NO_SYSTEM_PATHS=ON
  -D WITH_CODEC_FFMPEG=ON
  -D FFMPEG_LIBRARIES='avformat;avcodec;avutil;avdevice;swscale;rt;theoraenc;theora;theoradec;vorbis;vorbisenc;vorbisfile;x264;openjpeg'
  -D FFMPEG=/opt/lib/ffmpeg

Or even simpler, just run (in your blender-source dir):
  make -j2 BUILD_CMAKE_ARGS=" -D BOOST_ROOT=/opt/lib/boost -D Boost_NO_SYSTEM_PATHS=ON -D WITH_CODEC_FFMPEG=ON -D FFMPEG_LIBRARIES='avformat;avcodec;avutil;avdevice;swscale;rt;theoraenc;theora;theoradec;vorbis;vorbisenc;vorbisfile;x264;openjpeg' -D FFMPEG=/opt/lib/ffmpeg"

If you're using SCons add this to your user-config:
BF_PYTHON = '/opt/lib/python-3.3'
BF_PYTHON_ABI_FLAGS = 'm'
WITH_BF_OCIO = True
BF_OCIO = '/opt/lib/ocio'
WITH_BF_OIIO = True
BF_OIIO = '/opt/lib/oiio'
WITH_BF_CYCLES = True
WITH_BF_BOOST = True
BF_BOOST = '/opt/lib/boost'
BF_FFMPEG_LIB = 'avformat avcodec swscale avutil avdevice theoraenc theora theoradec vorbis vorbisenc vorbisfile x264 openjpeg'
BF_FFMPEG = '/opt/lib/ffmpeg'
WITH_BF_3DMOUSE = False


WARNING: If this script had to build boost into /opt/lib, and you are dynamically linking
         blender against it, you will have to run those commands as root user:

    echo "/opt/lib/boost/lib" > /etc/ld.so.conf.d/boost.conf
    ldconfig
</code>
</pre>
<h2> Before Compiling Blender </h2>
<p>Here I still select the easiest way to compile - cmake with default setup. However since we installed the boost library in /opt/lib/, instead of /usr/lib/ or /usr/local/lib/, we need to add this to the search path (as is mentioned at the end of previous message)<br />
<code><br />
echo "/opt/lib/boost/lib" > /etc/ld.so.conf.d/boost.conf<br />
ldconfig<br />
</code><br />
You may need sudo for these two commands.</p>
<h2> Compiling Blender </h2>
<p>Now it's ready to go, and switch to the source code folder of blender (in-source build)</p>
<pre>
<code>
make -j2 BUILD_CMAKE_ARGS=" -D BOOST_ROOT=/opt/lib/boost -D Boost_NO_SYSTEM_PATHS=ON -D WITH_CODEC_FFMPEG=ON -D FFMPEG_LIBRARIES='avformat;avcodec;avutil;avdevice;swscale;rt;theoraenc;theora;theoradec;vorbis;vorbisenc;vorbisfile;x264;openjpeg' -D FFMPEG=/opt/lib/ffmpeg"
</code>
</pre>
<h2> Notes </h2>
<p>If you have tried to do an in-source build, you should remove any CMakeCache.txt from the source code directory before actually running the out-of-source build</p>
<p>References:<br />
<a href="http://wiki.blender.org/index.php/Dev:2.5/Doc/Building_Blender/Linux/Ubuntu/CMake">Blender Wiki</a></p>
