---
layout: post
status: publish
published: true
title: Ubuntu + Latex + CJK + UTF8/GBK
author: Shihui Guo
author_login: yierbosimao
author_email: mr.shihuiguo@gmail.com
wordpress_id: 579
wordpress_url: http://www.guoshihui.net/?p=579
date: '2013-07-01 22:24:29 +0800'
date_gmt: '2013-07-01 22:24:29 +0800'
categories: blog
tags: []
comments: []
---
<p>It is always a bit mess to re-install these packages, so I decide to write a short tutorial for myself, also for anyone this might benefit.</p>
<p>Start from scratch, then you need to install latex (or texlive) and cjk package</p>
<pre>
sudo apt-get install texlive latex-cjk-all
</pre>
<p>After this, you should be able to compile a file using UTF-8 encoding. However, since the character library using UTF-8 encoding is far less than GBK, I went further to add GBK support.</p>
<p>There are two points you need to take care<br />
- save your file in GBK encoding, easiest and most likely to ignore<br />
- install GBK fonts, gives you most trouble here</p>
<p>Then let's install GBK fonts then. First download the program called gbkfonts (you may downlaod from <a href="http://www.ctex.org/documents/shredder/src/gbkfonts.gz">CTEX website</a>, in case it fails, download from this <a href="http://www.guoshihui.net/wp-content/uploads/2013/07/gbkfonts.gz">gbkfonts</a>).</p>
<p>Make sure you got Chinese fonts installed on your system, if not, install some free fonts</p>
<pre>
sudo apt-get install ttf-wqy-zenhei ttf-wqy-microhei
</pre>
<p>Unzip, make executable and move it to /usr/bin/ </p>
<pre>
gunzip gbkfonts.gz
chmod +x gbkfonts
sudo mv gbkfonts /usr/bin/
</pre>
<p>Make a folder under your home folder, and generate the gbkfonts inside this folder</p>
<pre>
mdkir ~/texmf
cd ~/texmf
gbkfonts /usr/share/fonts/truetype/wqy/wqy-zenhei.ttc hei
</pre>
<p>Then update the system paths to search for the fonts</p>
<pre>
sudo mktexlsr
sudo updmap
</pre>
<p>In some cases, you might want to try adding "Map cjk.map" to the following file before updmap command:</p>
<pre>
sudo vim /var/lib/texmf/web2c/updmap.cfg
</pre>
<p>By far you will be able to compile the latex files in GBK encoding</p>
