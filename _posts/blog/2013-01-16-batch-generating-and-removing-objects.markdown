---
layout: post
status: publish
published: true
title: 'Batch Generating and Removing Objects in Houdini '
author: Shihui Guo
author_login: yierbosimao
author_email: mr.shihuiguo@gmail.com
excerpt: "Here we write a simplest script in Houdini, to batch generating and removing
  objects.\r\n\r\nFirst there are three ways of using python in Houdini:\r\n- python
  shell\r\n- object parameter expression\r\n- python source editor\r\nThe major differences
  of these three are the previous two will load hou module by default, while the last
  not. However, the code you write in the python source editor will be part of the
  hou.session module. So if you meet the following error while you are writing your
  script in python source editor:\r\n\r\n<em>NameError: global name 'hou' is not defined</em>\r\n\r\nIt
  is actually because you didn't import Houdini modules, try adding this at the beginning
  of your script\r\n<code>\r\nimport hou\r\n</code>\r\n"
wordpress_id: 94
wordpress_url: http://www.guoshihui.net/?p=94
date: '2013-01-16 13:17:07 +0800'
date_gmt: '2013-01-16 13:17:07 +0800'
categories:
- blog
- cg
tags: []
comments:
- id: 81
  author: Kiko
  author_email: kovalewskiy@gmail.com
  author_url: ''
  date: '2013-06-16 07:06:11 +0800'
  date_gmt: '2013-06-16 07:06:11 +0800'
  content: Thanks that helpful!
---
<p>Here we write a simplest script in Houdini, to batch generating and removing objects.</p>
<p>First there are three ways of using python in Houdini:<br />
- python shell<br />
- object parameter expression<br />
- python source editor<br />
The major differences of these three are the previous two will load hou module by default, while the last not. However, the code you write in the python source editor will be part of the hou.session module. So if you meet the following error while you are writing your script in python source editor:</p>
<p><em>NameError: global name 'hou' is not defined</em></p>
<p>It is actually because you didn't import Houdini modules, try adding this at the beginning of your script<br />
<code><br />
import hou<br />
</code><br />
<a id="more"></a><a id="more-94"></a><br />
To add some variations to the scene, we make the box with random size and random position:<br />
<code><br />
import hou<br />
import random import randint</p>
<p>def makeflatbox():<br />
    num = 5<br />
    for i in range(num):<br />
	size = randint(1, 10)<br />
	pos = randint(1, 20)<br />
        flatbox = hou.node('/obj').createNode('geo')<br />
        flatbox.node('file1').destroy()<br />
        b = flatbox.createNode('box')<br />
        b.parm('sizey').set(size)<br />
	b.parm('tx').set(pos)</p>
<p>def removeallchild():<br />
    children = hou.node('/obj').children()<br />
    for child in children:<br />
        child.destroy()</b></pre>
<p></code></p>
<p>You can either copy and paste this code into the python source editor, or save as testBatch.py and put it into $Houdini_PATH/scripts/python/ Folder. $Houdini_Path by default will be $HIP, $HOME/houdiniX.Y ($HIH) and $HH. Then you can open your python shell and enter:<br />
<code><br />
import testBatch<br />
testBatch.makeflatbox()<br />
</code><br />
Now you should be able to see 5 boxes with different lengths and positions. Call another function in the shell to delete all objects:<br />
<code><br />
testBatch.removeallchild()<br />
</code></p>
<p>If you are editing your script on the fly and want to reload it frequently (surely you can close and reopen Houdini, haha, but never do that). use function reload(modulename):<br />
<code><br />
reload(testBatch)<br />
</code><br />
Then it will resource your script and all the changes since last resource will be effective.</p>
<p>Tips when you are writing in python:</p>
<blockquote><p>
Single line means expressions while multiple lines is the function body. So don't leave linebreaks inside a function
</p></blockquote>
