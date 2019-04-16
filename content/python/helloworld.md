---
title: "Python Hello World"
date: 2019-04-15T20:24:18-04:00
draft: False
---

<h2> by Matthew Barlowe</h2>
<br />
<p>"Hello World" is a very common first program for just about any
programming langauge. I'm sure there's some history behind it, but
I've never bothered to look it up. Usually it's just a simple program
of very limited lines that prints out the phrase "Hello World." The
purpose of this tutorial is to get you setup to write that first
program.</p>
<h2>Getting Started</h2>
<p>The first thing to do is open your favorite text editor. I use NeoVim
which is based on Vim a text editor that comes with Unix. Vim is know for
being dificult if you aren't used to it, but there are many others out
there: Nano and Emacs come with the MacOS Unix as well, you could use
Atom which is built by Github, or even plain old TextEdit. The main
thing is to use something that won't add extra unseen characters to
what you type like a word processor such as Microsoft Word or Apple
Pages.</p>
<p>Once you have your text editor open type these lines into them:

    #!/usr/bin/env python3

    print("Hello World")
Once that is done save your file as <code>helloworld.py</code> and exit the text editor if you are using
a terminal editor and type <code>python3 helloworld.py</code> which will
produce this output:
<pre><code class='python'>
Hello World
</code></pre>
Congratulations, you've just written your first python program! Obviously,
there's a lot more to it than this but even in just this simple program
you can learn a lot.</p>
<h2>Breaking Down the Code</h2>
<p>Ok let's look at the code and see what's going on in this program. The first
line of the code is what's called a shebang line. This isn't unique to
python scripts but is common in the Linux/Unix environment. A shebang line
tells the shell what type of interpreter to use to process the text of the
file. You can read more about shebangs and their use in \*nix[^1] envronments
[^1]: \*nix is a term commonly used to refer to operating systems based on the Unix
operating. This includes Unix, Mac OS X, Linux among others. Most usually it refers to Linux
and Mac OS X as those are the two most popular \*nix environments.
<a href='https://bash.cyberciti.biz/guide/Shebang' target="_blank">at this site</a>. Basically,
this line is telling Unix what type of python to use to run the script.</p>
<p>If you have followed my other tutorials you may be asking now, "Why did
you list <code>/usr/bin/env</code> instead of <code>/usr/bin/local</code>
where our Homebrewed python3 is located? An excellent question. The reason
we use <code>/usr/bin/env</code> instead of where our python is actually located
is because <code>env</code> is an actual Unix command that will create
an environment using the environment variables and then run the program passed
to it in the arguments which in this case is python3.</p>
<p>So the <code>env</code> will then use the <code>$PATH</code> variable, the
same one mentioned in the Homebrew tutorial, of the environment
and go down the directories on that <code>$PATH</code>until it finds the
right directory of the program which it then executes. To sum it all up
it just makes your code more portable because it will search that computer
to find where <code>python</code> is to exectue the script.</p>
<p>And one last thing the shebang is good for is letting people know exactly
what type of code they are looking at. It will say python3 if working with
version 3.x, python2 if working with version 2.x, and just plain python
if the code will run with either version. You won't have to worry about
python 2.x for much longer as it will soon be deprecated but there is
plenty of legacy code out there still.</p>
<pre><code class='python'>
print("Hello World")
</code></pre>
<p>The next part above is where the code actually starts doing something. In
this case that something is printing the phrase "Hello World." Now there are
a lot more things you can do than this in python, but <code>print</code> is one
of the most useful functions in python. <code>print</code> is the way python
outputs things to the terminal screen. You can read more about the function
<a href='https://docs.python.org/3/library/functions.html#print' target="_blank">here</a>.
You have now officially written your first program. While it doesn't seem
very impressive right now but the cliche of "a journey of a thousand miles
begins with just one step" applies here. Plus think of all the hard work
done just to get your system setup to get to this point. So keep plugging
along, and if you'd like to learn faster I suggest visiting
<a href='https://automatetheboringstuff.com' target="_blank">Automate the Boring Stuff</a> and reading
their really comprehensive tutorial to get you further along the path to
python mastery.</p>
<h2>Sources</h2>
<a href='https://unix.stackexchange.com/questions/103467/what-is-env-command-doing' target="_blank">What is env</a>
<br />
<a href='https://stackoverflow.com/questions/6908143/should-i-put-shebang-in-python-scripts-and-what-form-should-it-take' target="_blank">
What form should shebang take</a>
