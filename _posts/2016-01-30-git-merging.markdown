---
layout: post
title:  "GIT Merging with KDiff3"
date:   2016-01-30 17:50:00 -0800
categories: git merge kdiff3
---

Here's a brain dump of how to merge with GIT using KDiff3.

GIT Configuration Setup
-----------------------

To merge with git you will need to setup a few configuration options so that you can use a graphical merge tool.

1. Identify and locate the merge tool of choice:
* I use Kdiff3 for merging and the executable is located here: C:\Program Files\KDiff3\kdiff3.exe
2. Merge Tool Setup
* Configure GIT to use your merge tool by executing the following commands:
** `git config --global --add merge.tool kdiff3`
** `git config --global --add mergetool.kdiff3.path "C:\Program Files\KDiff3\kdiff3.exe"`

By default, GIT will save the original file as a *.orig after a successfull merge.  You can modify this behavior by executing the following command: `git config --global mergetool.keepBackup false`.  The merge tool itself, kdiff3, also has settings for keeping a backup copy.  Look in the options under the Directory tab.

All done with the GIT setup!

Note: If you had these configuration keys already set then the "–add" option will not succeed.  You can check what configuration settings you have setup by running "git config --global --list" and you can remove a configuration setting by running "git config --global --unset diff.tool"

Pre-merge Preparation
---------------------

Before actually merging you will need to make sure that both local branches are up to date.  To do this, checkout the source branch and perform a pull, then checkout the target branch and perform a pull.

Example: How to prepare to merge the dev branch into the feature/US101 branch.
	git checkout dev
	git pull
	git checkout feature/US101
	git pull

Merge Time
----------

Alright, all of the code is up to date and we're ready to actually perform the merge.
Execute this command: `git merge dev`

GIT will print to the console the list of files that are merged and if it was successfully auto-merged or if there was a conflict.  If there are no conflicts then GIT will have auto-committed everything and you are done, but if there is a conflict you will need to manually fix and resolve.

Conflict Resolution
-------------------

After a merge that has conflicts any file that is auto-merged successfully will be staged and any conflict will remain in the un-staged state awaiting your conflict resolution skills.

To resolve conflicts, execute this command: `git mergetool`

GIT will then list all conflicting files and run through them one by one giving you the opportunity to resolve them.  There are a couple scenarios that can play out during a conflict, but let's look at the two basic ones that can occur:

1. The two files are both modified

	GIT will launch your merge tool (kdiff3 in my case).  I resolve all conflicts using kdiff3, save the file, and close the tool.  The exit code of the tool will indicate to GIT that the conflicts were resolved and GIT will move that file into the staged area.  If you don't want to resolve the conflicts or just want to start over then just close the tool without saving the file and GIT will skip the file leaving it in the un-staged area where it would be picked up again the next time you run git mergetool.

2. The file was deleted in one branch and modified in another.

	GIT will prompt you on the command line to ask you if you wish to keep the file deleted, or keep the edited version of the file.  Simply respond to GIT via the command line and GIT will take the requested action and stage your changes.

Note: You can resolve conflicts on a single file by passing the mergetool command the filename!

Conclusion
----------

Hopefully this guide helps with conflict resolution in GIT...if only it was this easy at home with the family!