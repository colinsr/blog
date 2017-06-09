---
layout: post
title:  "Hello Jekyll!"
date:   2017-04-28 15:06:16 -0400
categories: jekyll
---
### This is my first post using jekyll.  
I've taken some notes during configuration of this on Windows 10 using the ubuntu linux subsystem but the <a href="https://jekyllrb.com/docs/installation/" target="_blank">documentation</a> on the site is pretty solid IMO.

This is more a collection of thoughts/brain dump than it is a guide for anyone looking for a step by step how to tutorial.  I can add one of those later.

I first configured an S3 bucket for static hosting with my custom domain.
I then downloaded wintersmith/js.  However, after a bit of looking around it seems to me that there is not enough support for that engine just yet so I started googling around some more.

I found a few prime candidates to use for my static site generator with my top 3 being:
* <span style="color: blue">__Jekyll__</span>
* Hexo
* Hugo

I decided on Jekyll due to the fact that it is well established and it's not wordpress.  I may play around with Hugo/Hexo at some point down the line.

This is the part of the story where I downloaded and configured jekyll.
It was a bit tricky to do this because Windows.  I chose to get it working using the linux subsystem on Windows 10.  Of course on the initial pass I inadvertantly hosed up the sudoers file, _bad Colin... you need to use visudo_, and had to scrap my linux install and start over.

I recently found out about "seamless" mode of VBox while following along with <a href="https://acloud.guru/learn/docker-devops-from-development-to-production"  target="_blank">Docker for DevOps - From Development to Production</a> on acloud.guru - thanks Nick I think this is freaking awesome.

I will probably start using VBox seamless mode all the time so that:
<ol type="A">
  <li>I can sharpen my linux skills</li>
  <li>I don't have to deal with the major PITA that Windows imposes for devs</li>
</ol>

Back to jekyll.
To config I followed the setup docs here:

[Jekyll Quickstart](https://jekyllrb.com/docs/quickstart/ "Quickstart")

In a nutshell:

~~~
gem install jekyll bundler
jekyll new cookiemonstercoding.com
cd cookiemonstercoding.com
bundle exec jekyll serve
~~~

At this point I got this error: 

`(jekyll 3.4.3 | Error:  Invalid argument - Failed to watch "/mnt/c/code/blog/cookiemonstercoding.com/.sass-cache/1b5e65ee1c1467ee48c61aa794c914e582856716": the given event mask contains no legal events; or fd is not an inotify file descriptor.)`

A minute of googling around brought me here:

https://github.com/jekyll/jekyll/issues/5233

Which suggested I add a `--force_polling` flag to bypass this error.

`bundle exec jekyll serve --force_polling` - worked like a charm.

After that my site became available at [http://localhost:4000](http://localhost:4000) and now I am free to manipulate the minima template.

