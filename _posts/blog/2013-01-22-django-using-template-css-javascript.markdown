---
layout: post
status: publish
published: true
title: django using template and static files (css, images, javascript)
author: Shihui Guo
author_login: yierbosimao
author_email: mr.shihuiguo@gmail.com
wordpress_id: 630
wordpress_url: http://www.guoshihui.net/?p=630
date: '2013-01-22 18:08:35 +0800'
date_gmt: '2013-01-22 18:08:35 +0800'
categories:
- blog
- django
tags: []
comments: []
---
<p><span style="color: #ff0000;">Please note: this is a note from my early experience of django and the method demonstrated here is not quite beautiful, especially you got several applications under the same project. Check out my new note.</span></p>
<p>=============================================================================================</p>
<p>So for the template, you need to edit TEMPLATE_URL in the settings.py</p>
<p>For css/javascript, django regards these as static files, make a static folder under the main folder, and use that to store your css/javascript files.</p>
<p>Before you can use them, you need to edit STATIC_URL and MEDIA_URL in the settings.py, such as<br />
<code><br />
STATIC_URL = '/static/'<br />
</code></p>
<p>Last step is to serve it when request comes, it is apache's job. Put the following two lines in apache website config file:<br />
<code><br />
Alias /media/ PROJECT_PATH/media/<br />
Alias /static/ PROJECT_PATH/static/<br />
</code></p>
<p>Then you can reference these static files in your template in this way:<br />
<code><br />
&lt;link rel="stylesheet" href="/static/css/style.css" type="text/css" /&gt;<br />
&lt;script type="text/javascript" src="/static/js/libs/jquery.min.js"&gt;&lt;/script&gt;<br />
</code></p>
