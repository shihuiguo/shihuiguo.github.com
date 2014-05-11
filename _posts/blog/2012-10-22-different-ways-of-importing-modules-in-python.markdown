---
layout: post
status: publish
published: true
title: Different Ways of Importing Modules in Python
author: Shihui Guo
author_login: yierbosimao
author_email: mr.shihuiguo@gmail.com
wordpress_id: 199
wordpress_url: http://www.guoshihui.net/?p=199
date: '2012-10-22 23:04:42 +0800'
date_gmt: '2012-10-22 23:04:42 +0800'
categories:
- blog
- python
tags: []
comments: []
---
<p>There are several ways for you to import modules into python, but they will determine how you can reference the attributes inside the modules. Take the math module for example:</p>
<ul>
<li> import math<br />
In this case, you are telling the interpreter that you are going to use the module, however the functions and constants in the module are not imported to the current namespace, which means you need to use math.pi, math.sin(), math.cos().... to reference all the functions in this module
</li>
<li>from math import pi, sqrt<br />
It imports math.pi, math.sqrt into current namespace, so you can use pi, and sqrt. But other module attributes (like sin, and cos) are not accessible.
</li>
<li>from math import *<br />
Then use pi, sqrt, cos, sin, and anything else defined by the module. However on one hand, there may exist conflicts between different modules containing functions with same names; on the other hand, it makes your code less readable. Another reason is that when you are debugging, all the global constants inside these modules will show up in your stackData, which makes it more difficult for you to find the variables you created.
</li>
<li>import math as m<br />
Then use m.pi. It's for both simplicity and clarity!
</li>
</ul>
<p>The choice is up to you!</p>
<p>Note, if you choose this way:<br />
<code><br />
import yourmodule<br />
</code><br />
After you made changes to the code on the fly, reload is like:<br />
<code><br />
reload(yourmodule)<br />
</code></p>
<p>If you only imported part of the module, say a function. What I did is to pop up the module from the system path, and then reload it. Anyone who knows a better solution, please leave a message to me<br />
<code><br />
import sys<br />
sys.modules.pop('yourmodule')<br />
from yourmodule import yourfunction<br />
</code></p>
