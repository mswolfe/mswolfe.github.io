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
5. Managing files
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
Ughh...I have to navigate the file system with only a keyboard.
<div>
Yes, but it is not that bad when you have:
* cd
* ls
* pwd
* pushd
* popd
</div> <!-- .element: class="fragment" -->
Note:
* cd, change directory
* ls, list directory contents
* pwd, print name of working directory
* pushd/popd, push/pop directory.
</script>
</section>

<section data-markdown data-separator-notes="^Note:">
## Moving around
In addition to those commands you also have the following handy built-in shell capabilities:
* Tab completion
* Shell expansion ('~' and '*')
* Clicky-clicky
* history
* alias
Note:
* Show tab completion
* '~' = home directory, cd ~
* '*' = match anything, ls receip*
* Selection with copy to clipboard, so left double click selects and copies, middle click will paste
* history command and how to access it via the up arrow and the '!' character
* alias (known under another name), via 'alias ..="cd .."'
</section>

<section data-markdown data-separator-notes="^Note:">
## Viewing files
* cat
* more
* less
* tail and it's super useful -f argument
Note:
* cat, concatenate file onto standard out
* more, file perusal filter
* less, opposite of more .. LESS IS MORE!
* tail, output the last part of a file
</section>

<section data-markdown data-separator-notes="^Note:">
## Managing files
* touch
* cp
* mv
* rm
* mkdir (-p)
* rmdir (rm -rf)
Note:
* touch, update timestamp and create
* cp, copy
* mv, move
* rm, remove files, can delete multi files at once.
* mkdir, -p = make parent directory as needed
* rmdir, not used much because of rm -r(recursive)f(force)
</section>

<section data-markdown data-separator-notes="^Note:">
## Editing files
* nano
* emacs
* vi
Note:
* These are your available editors.
* I will not go into these, but one is obviously better than the others.
* nano is very simple!
</section>

<section data-markdown data-separator-notes="^Note:">
## Searching files
* find
* grep
Note:
* find --type f --name bob
* grep -r(recursive) regex [files]
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
<script type="text/template" data-separator-notes="^Note:">
# Variables
BASH
<pre><code data-trim>
FOO="foo"
echo $FOO
</code></pre>
<div>
CMD PROMPT
<pre><code data-trim>
set FOO="foo"
echo %FOO%
</code></pre>
</div> <!-- .element: class="fragment" -->
Note:
Do you know what variables in cmd prompt look like?
</script>
</section>

<section data-markdown>
<script type="text/template" data-separator-notes="^Note:">
# Conditionals
BASH
<pre><code data-trim>
FOO="foo"
if [ "$FOO" = "foo" ]; then
   echo There seems to be a foo in your foo!
else
   echo Awwww, fooey!
fi
</code></pre>
<div>
CMD PROMPT
<pre><code data-trim>
IF %FOO% == "foo" (
   echo Why is my conditional delimited by a parenthesis?
) ELSE ( 
   echo This is not the foo you are looking for!
)
</code></pre>
</div> <!-- .element: class="fragment" -->
Note:
Do you know what conditionals in cmd prompt look like?
</script>
</section>

<section data-markdown>
<script type="text/template" data-separator-notes="^Note:">
# Loops
BASH
<pre><code data-trim>
for i in $( ls foo* ); do
	echo I found a file called: $i
done
</code></pre>
<div>
CMD PROMPT
<pre><code data-trim>
for %%G in (foo1.txt foo2.txt) do (
	echo I found a file called: %%G
)
</pre></code>
</div> <!-- .element: class="fragment" -->
Note:
Do you know what loops in cmd prompt look like?
</script>
</section>

<section data-markdown>
<script type="text/template" data-separator-notes="^Note:">
# Functions
BASH
<pre><code data-trim>
function foo {
	echo Mamma didnt raise no $1!
}
foo "bar"
</code></pre>
<div>
CMD PROMPT
<pre><code data-trim>
@echo Off
setlocal EnableDelayedExpansion
call :foo "bar"
exit /b

:foo
setlocal
echo Mamma didnt raise no %~1
endlocal
goto:eof
</code></pre>
</div> <!-- .element: class="fragment" -->
Note:
* Do you know what functions are in cmd prompt?  They are GOTOS!
* EnabledDelayedExpansion allows for loops to evaluate variables are runtime....as opposed to at interpertation.
* exit /b says exit the script and not the console...yeah...you can kill the console that some poor guy started.
* setlocal limits variables to the function scope, instead of global...global as in console global.
* goto:eof actually jumps to the end of the label and is how you end a function...
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
<script 	type="text/template">
## Why are you telling me this?
<div>
Imagine a world where:
</div> <!-- .element: class="fragment" data-fragment-index="1" -->
<div>
* every business requirement was written by a developer <!-- .element: class="fragment" data-fragment-index="2" -->
* every product owner that could not code was chased out of the building <!-- .element: class="fragment" data-fragment-index="3" -->
* the user interface is 100% functionally complete <!-- .element: class="fragment" data-fragment-index="4" -->
</div>
Note:
* What if i need to run this as a batch job?  What if I want to run this as a test?
* the user interface is at the tips of your fingers.
</script>
</section>

<section data-markdown data-separator-notes="^note:">
### Welcome to *nix where your dreams really can come true!
</section>

<section data-markdown data-separator-notes="^Note:">
## Resources
[Learn UNIX in 10 minutes](http://freeengineer.org/learnUNIXin10minutes.html)  
[Bash Guide for Beginners](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/)  
Note:
</section>