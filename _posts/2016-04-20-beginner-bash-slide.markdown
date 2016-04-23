---
layout: slide
title: Beginner Bash
description: A presentation slide detailing simple tips and tricks for using the BASH shell.
theme: black
transition: slide
categories: presentation bash beginner
---

<section data-markdown>
# Agenda
1. What is Bash?
2. Moving around
3. Viewing files
4. Creating &amp; Deleting
5. Editing files
6. Searching files
7. Write your own scripts!
8. Why is Bash so sweet?
9. Resources
</section>

<section data-markdown data-separator-vertical="^VerticalSlide" data-separator-notes="^Note:">
<script type="text/template">
## What is Bash?
Bash is a command line interpreter for the GNU Operating System.
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
Yes, but it is not that bad because of these tools: 
* pwd
* ls
* The '~' character
* The TAB key
* pushd
- popd
</div> <!-- .element: class="fragment" -->
Note:
Show how to use pwd, ~, tab, pushd, and popd
</script>
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
## Creating and Deleting
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

<section data-markdown>
## Write your own scripts!
Bash scripting has many well known features including:
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
for i in $( ls ); do
	echo item: $i
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
	echo Hello foo!
}
</code></pre>
Invoking foo is as easy as:
<pre><code data-trim>
> foo
> Hello foo!
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
## Why is Bash so sweet?
<span>
One word...<!-- .element: class="fragment" -->
</span>
<span>
ok, two words, but one pattern!<!-- .element: class="fragment" -->
</span>
<div>
Pipe &amp; Filter
[Pipes &amp; Filters](http://www.cs.olemiss.edu/~hcc/csci581oo/notes/pipes.html)
[Wikipedia](https://en.wikipedia.org/wiki/Pipeline_(Unix) "Wikipedia Pipeline")
<!-- .element: class="fragment" -->
</div>
Note:
Description about pipe and filter please.
</section>

<section data-markdown data-separator-notes="^Note:">
## Resources
Note:
Try to find some good beginner ones
</section>