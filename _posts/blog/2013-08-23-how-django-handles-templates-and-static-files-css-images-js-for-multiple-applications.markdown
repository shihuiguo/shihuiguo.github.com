---
layout: post
title: How Django handles templates and static files for multiple applications?
author: Shihui Guo
categories: [blog, django]
---
<p>Please note: this note is based on django 1.5</p>
<p>Say you got your project called MYPROJECT, and two applications: APPLE and BANANA in it. so your foler looks like:</p>
<pre>├── APPLE
│   ├── __init__.py
│   ├── models.py
│   ├── tests.py
│   └── views.py
├── BANANA
│   ├── __init__.py
│   ├── models.py
│   ├── tests.py
│   └── views.py
├── manage.py
└── MYPROJECT
    ├── __init__.py
    ├── settings.py
    ├── urls.py
    └── wsgi.py</pre>
<p><a id="more"></a><a id="more-637"></a><br />
First tip, put the templates and static files for each application inside each application folder, and the tree becomes like this:</p>
<pre>├── APPLE
│   ├── __init__.py
│   ├── models.py
│   ├── <span style="color: #ff0000;">static</span>
│   ├── <span style="color: #ff0000;">templates</span>
│   ├── tests.py
│   └── views.py
├── BANANA
│   ├── __init__.py
│   ├── models.py
│   ├── <span style="color: #ff0000;">static</span>
│   ├── <span style="color: #ff0000;">templates</span>
│   ├── tests.py
│   └── views.py
├── manage.py
└── MYPROJECT
    ├── __init__.py
    ├── settings.py
    ├── urls.py
    └── wsgi.py</pre>
<p>However before you dive into folder and put the static files directly there, use my second tip: use proper namespace, which basically mean:</p>
<pre>├── APPLE
│   ├── __init__.py
│   ├── models.py
│   ├── static
│   │   └── <span style="color: #ff0000;">APPLE</span>
│   │       ├── css
│   │       ├── images
│   │       └── js
│   ├── templates
│   │   └── <span style="color: #ff0000;">APPLE</span>
│   ├── tests.py
│   └── views.py
├── BANANA
│   ├── __init__.py
│   ├── models.py
│   ├── static
│   │   └── <span style="color: #ff0000;">BANANA</span>
│   │       ├── css
│   │       ├── images
│   │       └── js
│   ├── templates
│   │   └── <span style="color: #ff0000;">BANANA</span>
│   ├── tests.py
│   └── views.py
├── manage.py
└── MYPROJECT
    ├── __init__.py
    ├── settings.py
    ├── urls.py
    └── wsgi.py</pre>
<p>Because we added another level, so in your views.py for each application (take APPLE as example), you need to add this additional level as well:</p>
<pre>def index(request):
    # This is correct
    return  render(request, 'APPLE/index.html')
    # This commented is not correct
    # return  render(request, 'index.html')</pre>
<p>And to reference your static files in the templates (for example, index.html), do like this:</p>

![Image](../../images/code.png)

<p>So if you are under development, and using "python manage.py runserver" to test, all templates and static files should be successfully located by default. When I say by default, I mean these two default settings which tells django to look for templates and static files in each application:</p>


	STATICFILES_FINDERS = (
	    'django.contrib.staticfiles.finders.FileSystemFinder',
	    <span style="color: #ff0000;">'django.contrib.staticfiles.finders.AppDirectoriesFinder'</span>,
	#   'django.contrib.staticfiles.finders.DefaultStorageFinder',
	)

	TEMPLATE_LOADERS = (
	    'django.template.loaders.filesystem.Loader',
	    <span style="color: #ff0000;">'django.template.loaders.app_directories.Loader'</span>,
	#   'django.template.loaders.eggs.Loader',
	)


<p>But what you should do to serve the static files with apache? Normally static files are served by apache with following command</p>
<pre>Alias /static/ PATH_TO_STATIC_FOLDER</pre>
<p>So django provides another way, called collectstatic, which literally means collect all the static files from each application and put them under one folder. Open settings.py under MYPROJECT folder, and define the following variable:</p>
<pre># Put the absolute path of the folder where you want the collected files go. In this example, I put it beside the manage.py
STATIC_ROOT = 'PATH_TO_MYPROJECT/static/'</pre>
<p>Also make sure that 'django.contrib.staticfiles' is listed under INSTALLED_APP.</p>
<p>Then use manage.py to do the collection work:</p>
<pre>python manage.py collectstatic</pre>
<p>Then a collected folder /static/ will appear under the project main folder:</p>
<pre>├── APPLE
│   ├── css
│   ├── images
│   ├── js
│   ├── static
│   │   └── APPLE
│   │       ├── css
│   │       ├── images
│   │       └── js
│   └── templates
│       └── APPLE
├── BANANA
│   ├── css
│   ├── images
│   ├── js
│   ├── static
│   │   └── BANANA
│   │       ├── css
│   │       ├── images
│   │       └── js
│   └── templates
│       └── BANANA
├── MYPROJECT
└── static
    ├── APPLE
    │   ├── css
    │   ├── images
    │   └── js
    └── BANANA
        ├── css
        ├── images
        └── js</pre>
<p>By doing this, you only need to define one Alias for static files in Apache configuration!</p>
