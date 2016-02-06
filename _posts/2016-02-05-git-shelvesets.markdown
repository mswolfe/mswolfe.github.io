---
layout: post
title:  "GIT Shelvesets"
date:   2016-02-05 17:50:00 -0800
categories: git tfs shelveset
---

TFS has this fancy thing called a shelveset.  They take the selected pending changes in your workspace and save it to the centralized server with a title.

The purposes of a shelveset are:

1. Allow a developer to stash their changes for future retrieval while they work on a different feature.
2. Provides a way to backup your code if the TFS server is being backed up by your IT team.

This is a great feature provided by TFS, but what happens when the source code is being managed by GIT?

Stashing Changes
----------------

In GIT, #1 is handled by the "stash" command.  The GIT stash command takes your un-commited changes and stashes them in your local computer for future retrieval.  This allows the developer to work on a different feature until they are ready to apply the stash back on to a working branch.  Fantastic, but what about #2?

Backing up pending changes
--------------------------

It's a bit more work then how it is done in TFS, but it's possible.  Here's one approach to managing a shelveset in GIT:

1. Create a new branch called 'shelveset\\&lt;user.name&gt;\\feature_a' and check it out.
2. Commit all of your changes to this new local branch.
3. Push the branch up to the remote server.

Now, if you ever want to retrieve your changes you can do the following:

1. Checkout the working branch of choice.
2. Cherry-pick the last commit on the 'shelveset\\&lt;user.name&gt;\\feature_a' branch.  Remember, we don't really care about history...so don't merge, just perform a cherry-pick.
3. Reset the branch to un-stage all changes and you're ready to start working again!

Don't forget to clean up the branches in 'shelveset\\&lt;user.name&gt;' on the remote server once you're all done with them.

Automating shelvesets in GIT
----------------------------

One of the great things about GIT is that it is extensible and I've created a GIT command to do all of the steps listed above.  Download the git-shelveset script from the [git-shelveset](https://github.com/mswolfe/git-shelveset) repository and place it in the GIT installation folder that contains all of your GIT sub-commands.  My GIT sub-command folder is located at C:\Program Files (x86)\Git\libexec\git-core because I installed GIT as a standalone application from [https://git-scm.com/downloads](https://git-scm.com/downloads).

Now, in a GIT command prompt you should be able to issue the following commands:

* git shelveset help
* git shelveset list
* git shelveset save <shelveset_name>
* git shelveset apply <shelveset_name>
* git shelveset drop <shelveset_name>
* git shelveset clean

Final Notes
-----------

The GIT shelveset sub-command that I created is just creating branches on the remote server and then cherry-picking changes back onto a working branch for you.  The error checking in the git-shelveset command is extremely limited.  If things go wrong you may need to perform some manual clean up.  Feel free to log an issue on the github repository and I'll see if we can make the shelveset sub-command better!