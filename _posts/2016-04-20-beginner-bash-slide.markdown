---
layout: slide
title: Beginner *nix
description: A presentation slide detailing simple tips and tricks for using the BASH shell.
theme: black
transition: slide
categories: presentation bash beginner
---

<section data-markdown>
## Agenda
1. What is *nix?
2. What is Bash?
3. Moving around
4. Viewing files
5. Creating and Deleting files
6. Editing files
7. Searching files
9. But how do I...
10. Write your own scripts!
11. Pipe and Filter
12. Resources
</section>

<section data-markdown data-separator-notes="^Note:">
## What is *nix?
>A Unix-like (sometimes referred to as UN\*X or \*nix) operating system is one that behaves in a manner similar to a Unix system, while not necessarily conforming to or being certified to any version of the Single UNIX Specification.
>
> [Unix-like (Wikipedia)](https://en.wikipedia.org/wiki/Unix-like)
Note:
Any OS that is similar to Unix: Linux, FreeBSD, Solaris, OS X
</section>

<section data-markdown data-separator-notes="^Note:">
<script type="text/template">
## What is Bash?
Bash is a command line interpreter for many *nix Operating Systems.
<div>
Similar to CMD prompt in Windows...<!-- .element: class="fragment" -->
</div>
<div>
but way better...<!-- .element: class="fragment" -->
</div>
<div>
about 50 million times better...<!-- .element: class="fragment" -->
</div>
<div>
to be precise.<!-- .element: class="fragment" -->
</div>
</script>
</section>

<section data-markdown data-separator-notes="^Note:">
<script type="text/template">
## Moving around
Ughh...I have to navigate the file system with only a console and a keyboard.
<div>
Yes, but it is not that bad when you have:
* Tab completion
* Shell expansion ('~' and '*')
* history
* alias
</div> <!-- .element: class="fragment" -->
Note:
Show tab completion
Explain how '~' is expanded to mean your home directory
Explain how '*' is expanded to match things
Explain command history and how to access it via the up arrow and the '!' character
Explain how alias works, via alias ..="cd .."
</script>
</section>

<section data-markdown data-separator-notes="^Note:">
## Moving around
In addition to those built in shell utilties you also have the following handy commands:
* cd
* ls
* pwd
* pushd
* popd
Note:
Explain cd, ls, pwd, pushd, popd
</section>

<section data-markdown data-separator-notes="^Note:">
## Viewing files
* cat
* less
* more
* tail and it's super useful -f argument
Note:
Show how to use cat, less, more, tail -f
</section>

<section data-markdown data-separator-notes="^Note:">
## Creating and Deleting files
* touch
* rm
* mkdir (-p)
* rmdir (rm -rf)
Note:
Show how to use touch, rm, mkdir, rmdir.  Make sure to show rm using more than one file.
</section>

<section data-markdown data-separator-notes="^Note:">
## Editing files
* nano
* pico
* emacs
* vi
Note:
I will not go into these, but one is obviously better than the others.
</section>

<section data-markdown data-separator-notes="^Note:">
## Searching files
* find
* grep
Note:
Show off find and grep
</section>

<section data-markdown data-separator-notes="^Note:">
<script type="text/template">
## But how do I...
<div>
There are man pages, short for manual, for every command!  Try it for everything!
<pre><code data-trim>
$ man ls
$ man tail
$ man man
</code></pre>
</div>
</script>
</section>

<section data-markdown>
<script type="text/template">
## Write your own scripts!
<img data-src="{{ "public/beginner-bash-slide/bash_script_meme.jpg" | prepend: site.baseurl }}">
</script>
</section>

<section data-markdown>
<script type="text/template">
# Variables
<pre><code data-trim>
#!/bin/bash
FOO="foo"
echo $FOO
</code></pre>
</script>
</section>

<section data-markdown>
<script type="text/template">
# Conditionals
<pre><code data-trim>
#!/bin/bash
FOO="foo"
if [ "$FOO" = "foo" ]; then
   echo There seems to be a foo in your foo!
else
   echo Awwww, fooey!
fi
</code></pre>
</script>
</section>

<section data-markdown>
<script type="text/template">
# Loops
<pre><code data-trim>
#!/bin/bash
for i in $( ls foo* ); do
	echo I found a foo called: $i
done
</code></pre>
</script>
</section>

<section data-markdown>
<script type="text/template">
# Functions
<pre><code data-trim>
#!/bin/bash
function foo {
	echo Mamma didnt raise no foo!
}
</code></pre>
Invoking foo is as easy as:
<pre><code data-trim>
$ foo
Mamma didnt raise no foo!
</code></pre>
</script>
</section>

<section data-markdown>
<script type="text/template">
# WARNING!!!
Not all shells are equal!
<pre><code data-trim>
#!/bin/bash
function world {
	echo Explode!
}

if [ "bash" = "csh" ]; then
   world
fi
</code></pre>
</script>
</section>

<section data-markdown data-separator-notes="^Note:">
## Pipe and Filter
An architectural pattern that is found everywhere:
* Windows
* Linux
* OS X
</section>

<section data-markdown data-separator-notes="^Note:">
## Definition
> A filter is a program that takes a stream of text characters as its input and produces a stream of characters as its output.
>
> A pipe is a way of connecting two filters, in which the character stream output from the first filter is routed to the character stream input of the second filter.
>
> [Software Architecture](http://www.amazon.com/Software-Architecture-Foundations-Theory-Practice/dp/0470167742)
</section>

<section data-markdown data-separator-notes="^Note:">
<script type="text/template">
## Bash Example
<pre><code data-trim>
ls receipts* | grep -e VISA | sort
</code></pre>
<img data-src="{{ "public/beginner-bash-slide/filter-pipe.png" | prepend: site.baseurl }}">
Note:
Lists all files starting with "receipts" that contain the word VISA in order.  This is in essence an application.
</script>
</section>

<section data-markdown data-separator-notes="^Note:">
## Resources
[Learn UNIX in 10 minutes](http://freeengineer.org/learnUNIXin10minutes.html)  
[Bash Guide for Beginners](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/)  
Note:
</section>