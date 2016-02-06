---
layout: post
title:  "GIT WinMerge Setup"
date:   2016-01-15 17:50:00 -0800
categories: git diff winmerge
---

How to setup WinMerge as the GIT difftool
-----------------------------------------

GIT has built in support for using WinMerge as the difftool.  The only problem that I've found is that WinMerge doesn't handle added or deleted files correctly.  I found a script that fixes this issue and the following steps will detail how to set it all up.

1. Download the winmerge.sh at this [repo](https://github.com/mswolfe/git-utils/blob/master/winmerge.sh)
2. Move the winmerge.sh file into "C:\Program Files\Git\bin"

GIT Diff Tool Setup
-------------------

Configure GIT to use WinMerge by executing the following commands (You may need to use --replace-all instead of --add if you have previously set these settings):

* `git config --global --add diff.tool winmerge`
* `git config --global --add difftool.winmerge.path "C:\Program Files\Git\bin\winmerge.sh"`

By default, GIT will prompt you for each diff to confirm if you wish to diff the file.  You can bypass this behavior in two ways:

1. Pass the "-y" or "--no-prompt" option when you invoke "git difftool"
2. Turn it off globally by executing this command:
* `git config --global --add difftool.prompt false`

If you performed all of the steps above then you should see some handy output on the command line during the "git difftool" command and a nice blank panel when comparing against added/deleted files in WinMerge.