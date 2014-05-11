---
layout: post
status: publish
published: true
title: Setup A Git Server on Amazon EC2 for single user
author: Shihui Guo
author_login: yierbosimao
author_email: mr.shihuiguo@gmail.com
wordpress_id: 616
wordpress_url: http://www.guoshihui.net/?p=616
date: '2013-08-20 08:29:37 +0800'
date_gmt: '2013-08-20 08:29:37 +0800'
categories: [blog, git, ec2]
tags: []
comments: []
---
<p>This is the easiest way and only works for single user. If you are looking for multiple users, go for some more complex settings.</p>
<p>To make your life easier, add the public key to ssh default:<br />
<code><br />
ssh-add PATH_TO_YOUR_PERM_FILE<br />
</code></p>
<p>make a folder and setup the repo on the server:<br />
<code><br />
mkdri path_to_git_folder<br />
git init --bare reponame<br />
</code></p>
<p>Add the remote path to your existing repo (on your local machine):<br />
<code><br />
git remote add amazon username@ipaddress:/path_to_git_folder/<br />
</code></p>
<p>Then you can push or pull, but just to check if the setting is correct<br />
<code><br />
git remote update<br />
</code></p>
<p>After you pushed something to the remote repo, a good way to test is to try cloning it<br />
<code><br />
git clone username@ipaddress:/path_to_git_folder/<br />
</code></p>
