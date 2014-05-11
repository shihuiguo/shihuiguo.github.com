---
layout: post
status: publish
published: true
title: 'Running on a 32/64bit linux ? Or Processor? '
author: Shihui Guo
author_login: yierbosimao
author_email: mr.shihuiguo@gmail.com
wordpress_id: 139
wordpress_url: http://www.guoshihui.net/?p=139
date: '2013-02-17 23:24:20 +0800'
date_gmt: '2013-02-17 23:24:20 +0800'
categories:
- blog
- linux
tags: []
comments: []
---
<p>To tell if you are running a 32/64bit linux kernel, do:<br />
<code><br />
$uname -m<br />
</code><br />
If it returns i686, you got a 32bit linux; if it is x86_64, you got a 64bit one. Or in rare cases, you got i386, then 99 out of 100 you are running a 32bit.</p>
<p>To tell if you got a processor capable of supporting 32/64bit, do:<br />
<code wrap="false"><br />
$grep flags /proc/cpuinfo<br />
</code><br />
It will return something like:<br />
<code><br />
flags : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx <span style="color: #ff0000;"><strong>lm</strong></span> constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm<br />
flags : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx <span style="color: #ff0000;"><strong>lm</strong></span> constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm<br />
</code><br />
Look out for "lm", which means "long mode", or capable of 64bit. If you can't find it, you got CPUs that is only able to deal with 32bit.</p>
<p>Also a small hint, here it returns two rows of flags information, which means you got 2 cores (this is not surprising, right...).</p>
