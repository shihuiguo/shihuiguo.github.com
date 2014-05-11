---
layout: post
status: publish
published: true
title: Use Wing IDE to debug Maya Python Script
author: Shihui Guo
author_login: yierbosimao
author_email: mr.shihuiguo@gmail.com
wordpress_id: 481
wordpress_url: http://www.guoshihui.net/?p=481
date: '2013-04-11 14:37:26 +0800'
date_gmt: '2013-04-11 14:37:26 +0800'
categories:
- blog
- cg
- python
tags: []
comments: []
---
<p>The first thing I would like to point out is that for Wing IDE 101, there is no remote debugger/passive listen feature. This only applies in the case of Wing IDE Personal or higher licenses.</p>
<p>- copy the wingdbstub.py (originally in the installation of wing IDE) to the folder which contains your maya script<br />
- set kEmbedded=1 in the new wingdbstub.py<br />
- click on the bug icon in lower left of Wing's window and make sure that Passive Listen is enabled<br />
- use the debugger API to ensure the debugger is connected to the IDE before any other code executes as follows:<br />
<code><br />
import wingdbstub<br />
wingdbstub.Ensure()</p>
<p>After that, you should be able to reach breakpoints by causing the scripts to be invoked from Maya.</p>
