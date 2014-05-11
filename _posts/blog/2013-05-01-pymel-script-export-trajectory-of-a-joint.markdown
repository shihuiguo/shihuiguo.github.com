---
layout: post
status: publish
published: true
title: Pymel Script Export Trajectory of A Joint
author: Shihui Guo
author_login: yierbosimao
author_email: mr.shihuiguo@gmail.com
wordpress_id: 539
wordpress_url: http://www.guoshihui.net/?p=539
date: '2013-05-01 09:53:12 +0800'
date_gmt: '2013-05-01 09:53:12 +0800'
categories:
- blog
- cg
- python
tags: []
comments: []
---
<p>Perhaps I am reinventing the wheel, but I didn't find an existing maya function to do this and it seems easy enough to write some lines to do this. Hope this helps someone as well. If you can do this with existing "hidden" button, please let me know as well!</p>
<p>Also is there anyone who can tell me even if I use "import pymel as pm", I still need to use "pm.core.general.ls()" instead of "pm.ls()". I remembered that previously I can do the latter way, but this time it keeps poping up error and forced me to do the first one.</p>
<pre>
<code>
import pymel as pm

def _vector_2_string(vec):
        x = vec.x
        y = vec.y
        z = vec.z
        return str(x) + ' ' + str(y) + ' ' + str(z)

outstr = ""
f = open('ant.txt', 'w')
parent = pm.core.general.ls(selection = True)
for child in parent[0].members():
        childstr = child.name() + "\n"
        for iframe in range(50):
                pm.core.animation.currentTime(iframe, edit = True)
                childTr = child.getTranslation()
                childstr =  childstr + _vector_2_string(child.getTranslation()) + "\n"
        outstr = outstr + childstr + "End of Trajectory for One Endeffector"    
 
f.write(outstr)
f.close()    
</code>
</pre>
