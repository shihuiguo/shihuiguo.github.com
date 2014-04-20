---
layout: post
status: publish
published: true
title: Django on Apache with mod-WSGI in Ubuntu 12.04
author: Shihui Guo
author_login: yierbosimao
author_email: mr.shihuiguo@gmail.com
wordpress_id: 618
wordpress_url: http://www.guoshihui.net/?p=618
date: '2013-08-21 20:02:08 +0800'
date_gmt: '2013-08-21 20:02:08 +0800'
categories:
- Python
tags: []
comments: []
---
<p>Actually this is not that difficult. Suppose you already got your django and apache running separately.</p>
<p>First install the libapache2-mod-wsgi module<br />
<code><br />
sudo apt-get install libapache2-mod-wsgi<br />
</code></p>
<p>Go to your django project folder, make a subfolder called apache, and generate a wsgi file<br />
<code><br />
mkdir apache<br />
cd apache<br />
</code></p>
<pre>import os
import sys

sys.path.append('<strong>PATH_TO_DJANGO_PROJECT</strong>')

os.environ['DJANGO_SETTINGS_MODULE'] = 'settings'

import django.core.handlers.wsgi
application = django.core.handlers.wsgi.WSGIHandler()</pre>
<p>Now switch to apache side, add a new website config file under /etc/apache2/sites-available/</p>
<pre>
&lt;VirtualHost *:80&gt;

WSGIScriptAlias / &lt;strong&gt;PATH_TO_DJANGO_PROJECT&lt;/strong&gt;/apache2/django.wsgi
&lt;Directory &lt;strong&gt;PATH_TO_DJANGO_PROJECT&lt;/strong&gt;/apache2&gt;
Order allow,deny
Allow from all
&lt;/Directory&gt;
&lt;/VirtualHost&gt;
</pre>
<p>Now enable your website, and restart the apache, should be working now!</p>
<p>Note: please replace the variable PATH_TO_DJANGO_PROJECT with your own!</p>
