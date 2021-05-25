---
title: "IDEs of March"
date: 2020-03-13T01:39:30-04:00
draft: false
---

# IDEs of March

There are many articles about learning to code and mention where to learn
or how to learn etc. Very few however mention where you are going to write
the code once you learn it! Most beginner stuff have you working at that programming
language's terminal, which is great for getting the basics but you'll quickly grow past
that. So where does one actually write their source code? A lot of people use what's
called an IDE which stands for Integrated Development Envrionment.

# What's the Story Morning Glory

Codeacademy gives a [breif rundown](https://www.codecademy.com/articles/what-is-an-ide) and they
generally have these features: text editor, syntax highlighting, autocomplete, compiler(if needed),
and a debugger.

A text editor is the most important part. If you are completely new to coding, you are probably used
to writing things in some sort of program like Word or Apple Docs. These programs are completely useless
it comes to storing code because they have tons of metadata in the text that you don't see that
determines things like font size or type or margins etc. When you try to run this through a compiler
or an interpreter the program won't know what to do with them and will create an error that prevents
the script from running. A text editor in its most basic form is the basic notepad program for both Mac and Windows. IDE's just
take these editors and add a bunch of bells and whistles to them.

Syntax highlighting is a benefit where certain key words are highlighted so you can quickly parse the code.
These are usually syntax to create functions or classes. Comments often have a different color than executable
code. There are a lot of different color schemes for syntax highlighting. My favorite is [Molokai Dark](https://github.com/pR0Ps/molokai-dark)
and while it is a vim color scheme I'm pretty sure its been ported to the IDEs will talk about.

Autocomplete is more of argued about benefit of IDEs. Some people love it and some hate it. If you're just starting
out I would lean more towards using it because its good at helping you remember function/variable names in packages.
Some people hate it because it can get in the way when you are trying to code and autocomplete the wrong things if
they have similar names.

Unless you're writing a compiled langauge(C++, Java) then the built in compiler is not a huge issue. But even for
things like Python/R there will be built in terminals where you can run your code with leaving the IDE environment
which will be key to not breaking your concentration. Lastly there are debuggers, I personally don't use them because
I'm dumb but some people swear by them so being able to set break points for your code and stuff is really useful.

Now don't expect to download these and immediately get started coding as they do take some setup. For the most
part though its minimal to be able to start writing code to learn.

# So What are My Choices

There are quite a few choices out there some free, some not. This won't be an exhaustive list but there will be
enough choice to cover most of the people

## Visual Studio Code

[Visual Studio Code](https://code.visualstudio.com/) is what I recommend for just about everyone. It's free and open
source. Its backed by Microsoft so it won't stopped being maintained for now reason. And it has tons of plugins you can
download that will allow you to work with any language. It has full Git integration and a built in terminal as well allowing
you to run code without leaving the environment. It works on Windows/Mac/Linux as well so you can use it on any platform.
Visual Studio Code also has tons of customization so you can configure it to do almost anything you want once you get to that
point. If you're reading this to get "the best" IDE (no such things exists though!) then this would be my choice.

## Rstudio

The only time I disagree with what I said above is if you are going to be working in R then you need to use
[Rstudio](https://rstudio.com/products/rstudio/). Its not quite as customizable as VS Code in terms of packages
being developed by others, but it is probably the best IDE when work with code in a pure data evironment. It also
integrates with Git and has built in terminals and command line so you don't have to leave as well. Rstudio also
allows you to build [Rmarkdown files](https://rmarkdown.rstudio.com/) which is one of the easiest ways you can share
your findings as you can directly host them on [Rpubs](https://rpubs.com/) for free. If you work in R this is the easiest
way to build a portfolio to show to perspective employers

## Atom

[Atom](https://atom.io/) is another IDE developed by GitHub. It seems to be more tuned to frontend developers esepcially
those working in Javascript, but I have set it up to use Python and I'm sure it can be configured for almost every language.
It is also customizable by downloading user made packages like VS code. Technically Atom isn't a true IDE anymore but rather
a souped up text editor. But there are ways to add on those functionalities. Me personally I found Atom to be bloated and
clunky and it wouldn't be my first choice. But some people like it so I thought I would include it here.

## Others

### Python Spyder
[Spyder](https://www.spyder-ide.org/) is python's answer to Rstudio and like pandas to tidyverse it does enough but still feels
clunky. I haven't used it in a while so take what I say with a grain of salt but it wasn't my favorite. However if you want something
close to Rstudio, but don't want to work in R (completely understandable), this is the best best.

### Jetbrains

[Jetbrains](https://www.jetbrains.com/) makes a lot of good IDEs that are tailored to their individual langauge such as Pycharm for
python, IntelliJ for Java, and Datagrips for SQL. These are not free but I have used them and there are some key benefits to paying.
One is you don't have to rely on user created packages to add functionality and two you get actual support instead of having to scour
the internet to fix things. Again I feel VScode is just as good as these with a little extra work but if you don't want to put the time
in and have the money consider paying for a license for these.

# Only Read Past Here if You Are Truly a Masochist

So for the record I don't use any of these options for anything I do. Not. Use. A. Single. One. I actually craft my own IDE by combining a
bunch of different packages built around using [Neovim](https://neovim.io/) as my text editor. Neovim is an upgraded version of Vim which
was an improvment on Vi released in 1991. This is a text editor that has no mouse and you navigate around your code using entirely your
keyboard. It is not for the faint of heart and has a steep learning curve but if you have time to learn it you will be well rewarded
because Vim is a ubiqutous text editor that comes with all linux/unix systems and you'll never not be able to work.

In addition to neovim I install several packages to help me work. The first is [NerdTree](https://github.com/preservim/nerdtree) for navigating
directories of files. The next is [Airline](https://github.com/vim-airline/vim-airline) to improve my status bar. After that is
[Syntastic](https://github.com/vim-syntastic/syntastic) to handle all the linting for the languages I'm writing in. And lastly
[Supertab](https://github.com/ervandew/supertab) to handle my autocompletion. I've also used [Kite](https://kite.com/) for python things
which I really like as well.

All of this is dificult to setup and maintain so don't choose this until you feel you are ready. Honestly you may find you never want this
as Vim keystrokes can be added to almost any IDE these days. However if you find you want true customization of your text editor and IDE then
this is the only way to go. It is not for the faint of heart though and learning it is hard. However, if you decide to embark down this
path of darkness feel free to reach out to me and I'll try to help you as much as I can.




