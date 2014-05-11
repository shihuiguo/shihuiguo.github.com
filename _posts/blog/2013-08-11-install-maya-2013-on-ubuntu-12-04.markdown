---
layout: post
status: publish
published: true
title: Install Maya 2013 on Ubuntu 12.04
author: Shihui Guo
author_login: yierbosimao
author_email: mr.shihuiguo@gmail.com
excerpt: "Not sure how many persons are facing this trick, but if you go to Autodesk
  Education Community, select Maya for downloading, you would find the operating systems
  they support are only Mac and Windows. Want to get Maya running on linux?\r\n\r\nSo
  here is the way, it works on Ubuntu 12.04 for Maya 2013, but basically it should
  work for any other version of Maya and other Linux distros (Centos definitely).\r\n"
wordpress_id: 595
wordpress_url: http://www.guoshihui.net/?p=595
date: '2013-08-11 15:45:04 +0800'
date_gmt: '2013-08-11 15:45:04 +0800'
categories: [blog, cg, linux]
tags: []
comments: []
---
<p>Not sure how many persons are facing this trick, but if you go to Autodesk Education Community, select Maya for downloading, you would find the operating systems they support are only Mac and Windows. Want to get Maya running on linux?</p>
<p>So here is the way, it works on Ubuntu 12.04 for Maya 2013, but basically it should work for any other version of Maya and other Linux distros (Centos definitely).<br />
<a id="more"></a><a id="more-595"></a><br />
I have managed to hack a script <a href="https://dl.dropboxusercontent.com/u/26653411/guoshihui/maya4Ubuntu.sh">here</a></p>
<p>First, make a folder for downloading and processing the Maya package, such as:</p>
<p><code><br />
mkdir ~/mayaInstall<br />
cd ~/mayaInstall<br />
</code></p>
<p>download my script, and put it in the folder, make it executable and run</p>
<p><code><br />
chmod +x maya4Ubuntu.sh<br />
./maya4Ubuntu.sh<br />
</code></p>
<p>Theoretically, you only need to answer some pop-up message to make the magic happen. In case some of you are not familiar with that, some information you will need:</p>
<p>- license: student license still works, just register in the Autodesk education community, and you got a student license number.<br />
- at the end of the installation, there are some messages poping up, and tell you:</p>
<pre>
Finally, in order to have Composite run properly, make sure you make the
following changes.  If you are unsure about the procedure, please
contact your sys admin.

#su - root

Add the following line at the end, after the #@student line.

#vi /etc/security/limits.conf
#@student      -       maxlogins  4
*              soft    nofile     65536
*              hard    nofile     65536

#reboot

Once the machine has rebooted, login as root
# su - root
# tcsh
# limit
descriptors shall be set at 65536
</pre>
<p>Just do exactly what it says, and your maya should be working now!</p>
<p><a href="http://www.guoshihui.net/wp-content/uploads/2013/08/Screenshot-from-2013-08-11-162934.png"><img src="http://www.guoshihui.net/wp-content/uploads/2013/08/Screenshot-from-2013-08-11-162934-300x186.png" alt="Screenshot from 2013-08-11 16:29:34" width="300" height="186" class="alignnone size-medium wp-image-596" /></a></p>
<p>Credit:</p>
<p>The original script is from <a href="https://gist.github.com/daevid/4966741">https://gist.github.com/daevid/4966741</a>. I made some changes, including:</p>
<p>- not required root permission for the whole script, only for commands inside the script wherever needed. (This will not mess up your filesystem)</p>
<p>- remove some commands for defining and switching back and forth, this annoys me a bit and really got some limitations.</p>
