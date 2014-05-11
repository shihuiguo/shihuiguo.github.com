---
layout: post
status: publish
published: true
title: Watch Out When Undoing Things Under Git
author: Shihui Guo
author_login: yierbosimao
author_email: mr.shihuiguo@gmail.com
wordpress_id: 497
wordpress_url: http://www.guoshihui.net/?p=497
date: '2013-03-18 12:05:09 +0800'
date_gmt: '2013-03-18 12:05:09 +0800'
categories:
- blog
- git
tags: []
comments: []
---
<p><strong>Changing Last Commit</strong></p>
<pre>
$ git commit --amend
</pre>
<p>Example:</p>
<pre>
$ git commit -m 'initial commit'
$ git add forgotten_file
$ git commit --amend
</pre>
<p><strong>Unstaging a Staged File</strong><br />
Stage is an action which puts a file ready for putting into the repo (right after the add command). If you want to unstage a staged file, use:</p>
<pre>
$ git add .
$ git status
# On branch master
# Changes to be committed:
#   (use "git reset HEAD <file>..." to unstage)
#
#       modified:   README.txt
#       modified:   benchmarks.rb
#
</pre>
<p>Right below the “Changes to be committed” text, it says "use git reset HEAD <file>... to unstage". So, let’s use that advice to unstage the benchmarks.rb file:</p>
<pre>
$ git reset HEAD benchmarks.rb
benchmarks.rb: locally modified
$ git status
# On branch master
# Changes to be committed:
#   (use "git reset HEAD <file>..." to unstage)
#
#       modified:   README.txt
#
# Changes not staged for commit:
#   (use "git add <file>..." to update what will be committed)
#   (use "git checkout -- <file>..." to discard changes in working directory)
#
#       modified:   benchmarks.rb
#
</pre>
<p><strong>Abandoning your modifications since last commit</strong><br />
The same example used in <em>Unstaging a Staged File</em>, we want to abandon the modifications on benchmarks.rb, but keep the modifications on README.txt. simply do:</p>
<pre>
$ git checkout -- benchmarks.rb
$ git status
# On branch master
# Changes to be committed:
#   (use "git reset HEAD <file>..." to unstage)
#
#       modified:   README.txt
#
</pre>
<p>When you got multiple files to reset, go</p>
<pre>
git checkout -- .
</pre>
<p><strong>Going back to previous commits</strong><br />
Sometimes, you wanna have a look of previous versions, but keep the current one. The first thing you need to do is to save, stage and commit modified files (don't worry if you are half-way of your work, use the amend command to fix the commit). Then you checkout previous commit:</p>
<pre>
git checkout hashID
</pre>
<p>Or checkout this commit as a new branch, this is useful because you can make changes on independent branch. If successful, you can merge the branch back, if not then simply abandon that branch. To checkout this commit as a new branch, do:</p>
<pre>
git checkout -b newbranchname hashID
</pre>
<p><strong>Abandon Your Commits</strong><br />
When I say abandon, I mean throwing them away totally, and this is pretty dangerous and cant' be recovered. Be careful with this command:</p>
<pre>
git rebase -i hashID
</pre>
<p><strong>Delete Your Branches</strong><br />
Delete your local branch</p>
<pre>
git branch -d the_local_branch
</pre>
<p>Delete remote branch</p>
<pre>
git push origin :the_remote_branch
</pre>
