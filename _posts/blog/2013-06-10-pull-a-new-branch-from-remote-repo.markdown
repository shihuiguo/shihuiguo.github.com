---
layout: post
status: publish
published: true
title: Pull a new branch from remote repo
author: Shihui Guo
author_login: yierbosimao
author_email: mr.shihuiguo@gmail.com
wordpress_id: 561
wordpress_url: http://www.guoshihui.net/?p=561
date: '2013-06-10 09:09:00 +0800'
date_gmt: '2013-06-10 09:09:00 +0800'
categories:
- blog
- git
tags: []
comments: []
---
<p>The <span style="color: #ff0000;">wrong</span> way to do is:</p>
<pre>
git checkout -b new_branch
git pull origin new_branch
</pre>
<p>But please do it in this way:</p>
<pre>
git checkout -b new_branch origin/new_branch
</pre>
<p>Though seemingly the same, these two ways are significantly different:<br />
The first one checkout the new branch from existing branch (maybe master), and merge it with the remote new_branch, this is not really what we want<br />
The second does the clean job, just set up to track the remote new_branch and got nothing to do existing local branch.</p>
<p>But if you meet the following error:</p>
<pre>
fatal: git checkout: updating paths is incompatible with switching branches.
</pre>
<p>This error occurs mostly because you want to check out a branch which your local git repo is not aware of, which means the remote branch is totally new. So update the local git repo before checking out the new branch:</p>
<pre>
git remote update
git checkout -b new_branch origin/new_branch
</pre>
