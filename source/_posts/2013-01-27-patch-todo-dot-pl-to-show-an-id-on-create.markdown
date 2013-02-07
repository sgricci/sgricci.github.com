---
layout: post
title: "Patch todo.pl to show an ID on create"
date: 2013-01-27 09:23
comments: true
categories: ['software','perl','todos'] 
---

I'm a command line junkie.  I spend most of the day in command-line based tools (vim, git, mysql, etc.).  I rarely ever use anything with a gui besides a browser.

I love using [sprint.ly](http://sprint.ly), it's an awesome tool for agile development. Sadly it doesn't have a command line tool, and no one has created one yet.  When I'm hacking away on a personal project and I want to keep a rolling todo list, I use todo.pl (which uses the [hiveminder](http://www.hiveminder.com) API for a backend.)  Sadly, the default todo.pl script (which can be installed via CPAN btw) is pretty terse.  I add a task, and I want to immediately perform some additional task to it, such as adding tags, etc. So I've patched my todo.pl to display the task ID after adding it, here's what I changed.

Open todo.pl (you can find it using `whereis todo.pl`) and locate the response_ok line for the sub `add_task` (line 357 on mine), change that line to this:
         result_ok($result, "Created task: #".$result->{_content}->{record_locator});

*Note: You'll need root to edit this file if it's installed globally*

Now, it'll respond with `Created Task: #XXXX`, much more useful for me.

--s
