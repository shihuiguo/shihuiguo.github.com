---
layout: post
title: Importing Numpy and Scipy into Maya 2014 on CentOS 6.5
description: A hack way
category: blog
---
You may want to use numpy and scipy in maya to do some matrix operations or solve some odes, but unfortunately maya doesn't support these two python modules at this moment. If you google, most people will tell you to recompile the source and import into maya. 

I don't want to recompile from the source so looking for an alternative. It may work or not for you guys, but let me know.

First install numpy and scipy on your machine first, on CentOS, you do:
	sudo yum -y install gcc gcc-c++ numpy python-devel scipy

Then open the script editor in maya and add the path where you just installed numpy and scipy
	import sys
	sys.path.append('/usr/lib64/python2.6/site-packages')

If you are not sure where your numpy and scipy are installed, do
	locate numpy

Then you can import numpy in the script editor:
	from numpy import *

There maybe some conflicts since CentOS is running 2.6 and Maya is running 2.7, so it's just a hack way. You better be prepared for some werid things to happen.





