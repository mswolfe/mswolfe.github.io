---
layout: post
title:  "GIT Your Diff Pimped"
date:   2016-07-14 17:50:00 -0800
categories: git pimp diff compactionHeuristic diff-so-fancy
---

[GIT](https://git-scm.com/downloads) was recently updated to version 2.9 and GitHub posted a blog article about some of the changes [here](https://github.com/blog/2188-git-2-9-has-been-released).  The section about "Beautiful diffs" really got me excited and I decided to pimp my command line diff capabilities from what I had read.  The following are the steps I took to change the boring old command line diff into a thing of beauty.

* Configure GIT to use the new experimental compactionheuristic feature.
* Install diff-so-fancy

# Configure compactionHeuristic

This part was easy; open up GIT bash and run the following command:

	git config --global --add diff.compactionHeuristic true

Done!

# Install diff-so-fancy

You can find diff-so-fancy right [here](https://github.com/so-fancy/diff-so-fancy).  There are a couple of  ways to install this tool, but I already had [Node.js](https://nodejs.org/) installed and the npm route was just plain simple.

Run the following command to install diff-so-fancy via npm:

	npm install -g diff-so-fancy

I configured the diff-highlight colors as suggested by diff-so-fancy using the following commands:

	git config --global color.diff-highlight.oldNormal "red bold"
	git config --global color.diff-highlight.oldHighlight "red bold 52"
	git config --global color.diff-highlight.newNormal "green bold"
	git config --global color.diff-highlight.newHighlight "green bold 22"

Finally, I configured GIT to use diff-so-fancy as my pager so that every diff looks even better than the last!

	git config --global core.pager "diff-so-fancy | less --tabs=4 -RFX"

# Diff Everything

It's pretty easy, but those few steps above made a huge difference in my command line diffing.  I barely use my difftool anymore because these command line diffs are so gorgeous!

Checkout the difference those minor tweaks can make to your command line diff below:

First, here is a plain diff with no modifications: ![Plain GIT diff](/public/git-pimpdiff/PlainDiffNoHeuristic.png)

Second, here is a diff with the compaction heuristic enabled: ![GIT diff with compaction heuristic](/public/git-pimpdiff/PlainDiffWithHeuristic.png)

Third, here is the same diff with compaction heuristic and diff-so-fancy installed: ![GIT diff with compaction heuristic and diff-so-fancy](/public/git-pimpdiff/DiffSoFancy.png)

Lastly, here is a bonus shot of diff-so-fancy where it is highlighting the exact characters on the line that changed; very fancy: ![GIT diff with diff-so-fancy showing off character differences](/public/git-pimpdiff/DiffSoFancy2.png)
