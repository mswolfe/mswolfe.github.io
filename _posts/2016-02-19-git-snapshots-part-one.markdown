---
layout: post
title:  "GIT Snapshots Part 1"
date:   2016-03-04 17:50:00 -0800
categories: git basic lesson snapshot camera pictures
---

Foreward
========

My company has been slowly, ever so slowly, transitioning from TFS to GIT over the last few months.  I'd like to say that I'm a GIT master, a GIT magician, a GIT guru and the upper management recognized this fact by instantly putting me in charge of the GIT transition project.  Sadly, I am not a GIT magician and they did not put me in charge of the GIT transition project.  Luckily, they did put me on the first project that transitioned to GIT...both lucky for myself and the company!  It has given me a really great opportunity to learn more about GIT and allowed me to help guide the company in its best practices.  So, it is because of my previous experiance and my role on the first GIT project that I have been recogonized as the "GIT" guy in our department.

After being the "GIT" guy 

Without further ado, here is how i have been trying to teach GIT with great success at my company.

Part 1 - How to take a picture
==============================
TFS, SVN, and of course GIT are all revision control systems.  What does that mean?  Let's look at the formal definition of revision to try to get are hands around it.

> Revision: the action of revising.
> 
> Revise: reconsider and alter (something) in the light of further evidence.

Great, so all of these systems are used to control the alteration of something!  Pack it up, let's go home, it should all be clear to you now.  All joking aside, that really is what these systems do, but it seems to be such an abstract thought for many people it is really hard to understand.  Let's imagine that you are on vacation in Hawaii and you brought your HDSLR 24 Jigawatt camera.  You arrive at the airport and you take your first picture of yourself eating that delicious airport breakfast burrito.  Then you arrive in Hawaii and you snap a picture of yourself receiving your first lei.  Finally, on your last night you attend a luau and nab a picture of yourself with that really cute dancer!  Nice, you've got three pictures, in chronological order, stored on your camera when you get home.  Perhaps you are disappointed with yourself that you only took three pictures during your Hawaiian vacation, but for a basic example to work with we're pretty content.

Alright, we've got three pictures and each one is a different moment in time and our fancy camera actually captured a bunch of attributes about each picture.  We have attributes like the time at which the picture was taken, the resolution of the picture, the geographic location of where the picture was taken.  This is great, but it doesn't really do me much good if I can't look at the pictures!  Never fear, as our HDSLR 24 Jigawatt camera also has a built in screen that allows me to view a picture.  It is so awesome that I can even control which picture I am viewing with some simple buttons and since the pictures are chronologically ordered I feel like I am moving backwards and forwards in time

![Our vacation pictures in diagram form]({{ site.baseurl }}/assets/git-snapshots-part-one/GIT_Basic_Commits.svg)

To recap, the HDSLR 24 Jigawatt camera can capture moments in time with extra attributes and it allows you to control which moments of time you view.  I'm going to say that this fancy camera is actually a revision control system!  You are the "something" being altered by time in every picture and the camera is letting you control which versions of yourself you see.  This is basically what revision control systems are but to files in a folder instead of pictures in a camera.  You are picking related changes to group together instead of aiming the camera to find the right scenery.  You are commiting the related changes instead of pressing the button on the camera.  Finally, you are using the revision control system to view the state of the files at different points in time instead of using the simple buttons on the camera to view different pictures.

GIT Basics
----------
Hopefully the camera example above gave you different perspective on revision control systems.  Let's dive into some of the basic GIT commands to see how we can use GIT just like we used our camera.

### The big bang
git init
Before we can start taking pictures we need to start the clock!  

### Aim the camera
git add

### Take a picture
git commit

