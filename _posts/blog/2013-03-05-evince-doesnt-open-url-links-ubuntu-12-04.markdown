---
layout: post
status: publish
published: true
title: Evince Doesn't open URL links (Ubuntu 12.04)
author: Shihui Guo
author_login: yierbosimao
author_email: mr.shihuiguo@gmail.com
excerpt: "After upgrading my ubuntu from 10.04 to 12.04, the evince cannot open url
  links in either firefox or chrome. This seems to be a bug, see:\r\n<code>\r\nhttps://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/964510\r\nhttps://bugs.launchpad.net/apparmor/+bug/605586\r\n</code>\r\n\r\nTo
  fix this, adding the following to /etc/apparmor.d/abstractions/ubuntu-helpers:\r\n"
wordpress_id: 251
wordpress_url: http://www.guoshihui.net/?p=251
date: '2013-03-05 23:32:23 +0800'
date_gmt: '2013-03-05 23:32:23 +0800'
categories:
- blog
- linux
- latex
tags: []
comments: []
---
<p>After upgrading my ubuntu from 10.04 to 12.04, the evince cannot open url links in either firefox or chrome. This seems to be a bug, see:<br />
<code><br />
https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/964510<br />
https://bugs.launchpad.net/apparmor/+bug/605586<br />
</code></p>
<p>To fix this, adding the following to /etc/apparmor.d/abstractions/ubuntu-helpers:<br />
<a id="more"></a><a id="more-251"></a><br />
<code><br />
 /usr/lib/chromium-browser/chromium-browser-sandbox PUxr,<br />
  /opt/google/chrome/chrome-sandbox PUxr,<br />
  /opt/google/chrome/google-chrome Pixr,<br />
  /opt/google/chrome/chrome Pixr,<br />
  /opt/google/chrome/lib*.so{,.*} m,<br />
</code><br />
Then do<br />
<code><br />
sudo apparmor_parser -r -W -T /etc/apparmor.d/usr.bin.evince<br />
</code></p>
<p>After doing this, when I click a href in evince, they can be successfully directed to chrome and open the correct page. lol</p>
