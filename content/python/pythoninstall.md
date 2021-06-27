---
title: "Installing Python"
date: 2019-04-15T19:25:14-04:00
draft: False
---

<h2> by Matthew Barlowe</h2>
<br />
Ok so if you've read the

[Homebrew Tutorial]({{< relref "unix/homebrew">}})
you are
ready to actually start using it to start programming in python. If you haven't
read that tutorial and you want to follow this one I sugestt going
back and reading that one first. First though we need to get your system
properly setup to run python safely and avoid problems in
the future.  The first step to doing that is to install Apple's Xcode utilities,
specifically GCC. If you already have Xcode installed you will not need to do this
as it will cause issues. In the terminal just type <code>xcode-select --install</code>
if you have Mavericks or higher MacOS. If you are using Mountain Lion or Lion
you'll need to visit <a href='https://developer.apple.com/downloads/'>Apple's Developer Site</a>.
You can read more about it by reading this Github <a href='https://github.com/kennethreitz/osx-gcc-installer#readme'>
README</a>.
<h2>Brewing Python</h2>
<p>After that's done the next step is to type <code>brew install python3</code>
into the terminal and hit enter and you'll start to see something like this begin to print out
on the screen:</p>
<div class='fitimage'>

![Homebrew installing](/python/brew.png)

</div>
<p>Once Homebrew is finished running you should be good to go and are now able to start
running python.  Yes it was that easy, amazing isn't it! Let's check and make sure
you're up and running by typing <code>python3</code> into the terminal and hit enter.
You should see the Python version come up (which should be 3.6.4) and then a prompt that
looks like this <code>>>></code>. Once that pops up type <code>exit()</code> and return
back to the terminal.</p>
<p>Now that's python is setup lets get some python packages installed that will
be very important in making things go smooth in your programming future. We will
do this by using <code>pip</code>. Pip is similar to Homebrew in that it is a package
manager except it only manages packages that relate to python. This will be the main
way you install extra programs for python that are not included in the base python packages.
Type this command
into your terminal <code>pip install virtualenv virtualenvwrapper</code>.  These two
packages are important because they allow you to install virtual envrionments which I'll
get into later on in this tutorial.</p>
<p>Once those are installed the next step is to type <code>nano ~/.bash_profile</code> into
the terminal and hit enter. This will open the nano text editor and create the <code>
.bash_profile</code> file if you don't have one created. <code>.bash_profile</code> is
a file that tells your terminal (i.e. a bash shell) what to do everytime you open a new window.
You can set environment variables create keyboard shortcuts aka aliases and lots of
other things that are beyond the scope of this article.  But for now you need to add
these four lines to make sure virtualenvwrapper will work properly:
<br />
<br />
<code>
#Setup Virtualenvwrapper environment variables<br />
export WORKON_HOME=$HOME/.virtualenvs<br />
export PROJECT_HOME=$HOME/Devel<br />
export VIRTUALENVWRAPPER_PYTHON=/usr/local/bin/python3.6<br />
source /usr/local/bin/virtualenvwrapper.sh<br />
</code>
<br />
The first line is just a comment to let others know what is going on. The next line creates
whats called in Unix/Linux an environment variable that is mapped to the <code>.virtualenvs</code>
directory located in your home directory. This is where all your virtual environments are stored
that virtualenvwrapper keeps track of. The <code>export</code> command tells your bash shell
to create this environment variable everytime you open a new bash window in the terminal.
The next line are where the virtualenvwrapper projects will be stored.  We won't be touching on
those in this tutorial.</p>
<p>The fourth line tells virtualenvwrapper where to look for python
when it is creating a new virtualenv. Remember from the Homebrew tutorial that our brewed
python is in <code>/usr/local/bin</code> so that's where we want our virtualenvwrapper to
look when creating a new python environment and not in <code>usr/bin</code>. The last line
tells bash to run the virtualenvwrapper shell script everytime you open a terminal window
so that you can use virtualenvwrapper. Once you've typed that exactly as it appears in
the nano window hit `Ctrl+o` and then enter to save. Once save hit `Ctrl+x` to exit.</p>
<p>Now you should be back at the command line. Next just close the window you were in
and open a new one and should see these lines appear in the terminal:</p>
<div class='fitimage'>

![virtualenvwrapper installing](/python/virtualenvwrapper.png)

</div>
<p>That means the virutalenvwrapper bashscript is running and installing the directories neccesary
to get things up and running. To check and see type <code>workon</code> which if everything is
working right should return nothing because we haven't created any virtual environments. Now
type <code>mkvirtualenv temp</code> which will create a new virtual environment named temp.
Type <code>workon</code> again and now it should show <code>temp</code> in the list of virtual
environments on the computer. If you've been able to complete all that good job! The hardest
part is over and now you are ready to being coding in earnest.</p>
<p>So why virtualenvwrapper over virtualenv or other virtual environments? One reason is
that it stores your virtual environments in one location and allows you to acces those no
matter where you are in the file structure without typing long filepath names or creating aliases
in <code>.bash_profile</code>. With <code>virtualenv</code> you have to provide the file path
of the location of the virtual environment in order to activate it; by using <code>virtualenvwrapper</code>
you avoide all the trouble of typing out those filepaths. Another benefit is that <code>virtualenvwrapper</code>
keeps track of all the environments you have created so in case you forget the name of one you can just
type <code>workon</code> and get a list of all the environments you have ever created.
<h2>Navigating Your Pythons</h2>
<p>You should now have two Pythons installed on your Mac if you've followed the instructions:
the Apple supplied python 2.7 and the python 3.6 which you brewed with Homebrew. These two pythons
are accesed in two different ways:<br />
<br />
<code>python</code><br />
This will access the Apple installed Python. <br />
<br />
<code>python3</code><br />
This will access the brewed installed python version 3.6.
There will also be two different <code>pip</code> that will handle your python
packages:<br />
<br />
<code>pip</code><br />
This pip will install packages to the MacOS python.<br />
<br />
<code>pip3</code><br />
And this pip installs packages to our brewed python 3.6.<br />
<br />
~~Don't worry if you type pip instead of pip3 the way this is setup you'll get an error
message because it will try to install the package in <code>/usr/bin</code> which
as I noted in the Homebrew tutorial is protected. This will happen <b>UNLESS</b>
you run <code>pip</code> using <code>sudo</code>. Don't do that. You may read other
articles saying to do that. Don't. Unless you know what you're doing, and if you're
reading this you don't. Don't use sudo. If you run pip with out sudo and it works
it means you are logged in as a superuser by default which I suggest you change.~~</p>

**Edit: 2019-04-15**
I just recently installed python on a new Mac system. It seems that Homebrew now aliases
`pip` to be the same as `pip3`. However to make sure enter `which pip` and the output should
be `/usr/local/bin/pip` which means `pip` is aliased to the correct pip. If the result is
`/usr/bin` that means `pip` is still tied to the system python and you should only use `pip3`
<h2>Creating Virtual Environments</h2>
<p>Ok so now you've got your python setup and you have the ability to create virtual environments.
But why shoud you use virtual environments? That's a good question, and the benefit of
a virtual environment is it's ability to isolate a python install and the packages associated with
it from other pythons and other packages. Whenever you create a new virtual environment
you are creating a fresh python almost the same as if you brewed python for the very first time
on your system.  Unless specified the python in the virtual envrionment will only come with
the base packages that come with python itself.</p>
<p>So any package you <code>pip install</code> will only be found in <b>THAT</b> virtual
environment. This is important because packages can conflict at any time and cause scripts
that would run normally to break, throw errors, or behave differently. And the package could
not even be broken it could just update and change the syntax of a function that you imported.
So what, just not update that one package? But what if you have another script that needs that
updated package? You can't have two version of the same package running side by side because that
will cause issues as well since python won't know which exact one you want. This is where
virtual environments come in.
<p>Virtual environments allow you to maintain two completely different versions of however many
packages you want without any problems at all. You just keep them in seperate environments and
switch between them as you need to run the neccesary python scripts. In the beginning this won't
be a big deal, but its a good habit to get into as it's much easier to track down a bug or
determine the source of an issue and then fix it inside of a virtual envrionment.</p>
<p>So now that you know why to use virtual environments, the question is how? You've already seen
a little bit when we were installing and testing <code>virtualenvwrapper</code> but we'll go
over the main ones again:</p>
<p><code>mkvirtualenv [environment_name]</code><br />
<br />
This will create a virtual environment with whatever name you give it.  <code>mkvirtualenv test</code>
will create a virtualenv named test.<br/>
<br />
<code>workon</code><br />
<br />
This command will switch between environments. <code>workon test</code> will switch to the test
virtual environment. If you also just type <code>workon</code> it will list all the virtual
environments you have created.<br />
<br />
<code>deactivate</code><br />
<br />
This will exit you out of the current virtual environment you are working in.<br />
<br />
<code>rmvirtualenv [environment_name]</code><br />
<br />
This will remove the named environment. <code>rmvirtualenv test</code> will remove the test virtual
environment.</p>
<p>One last thing about virtual environments is that you don't need to worry about which
<code>pip</code> you need to use while in one. <code>pip</code> automatically maps to the <code>pip</code>
installed with the virtual environment.</p>
<h2>Installing Python 2.7</h2>
<p>If you're new to python you probably don't need to worry about this, but just in case you do need to
I'll quickly go over installing python 2.7. If you've followed all the steps covered so far in the tutorial
the next thing you need to type in the terminal is <code>brew install python2</code>. This will bring up the
familiar brew screen from before.  Once thats installed, to access the brewed python you will need to use
<code>python2</code> instead of <code>python3</code>. The same for pip it will be <code>pip2</code> instead
of <code>pip3</code>. To create a python 2.7 virtual environment will also be a little different as well
as you will need to tell the virtualenv to use python 2 with the <code>-p</code> flag: <code>mkvirtualenv -p python2 python2env</code>
<p>If you have any questions feel free to email me at barloweanalytics@gmail.com make sure you give me OS specs and any error outputs/screenshots
so that I can diagnose your problem as quick as possible.
<h2>Sources:</h2>
<a href='https://docs.brew.sh/Homebrew-and-Python.html'>Homebrew Python Install Docs</a>
<br />
<a href='http://virtualenvwrapper.readthedocs.io/en/latest/install.html'>Virtualenvwrapper Docs</a>
<br />
<a href='http://www.linfo.org/path_env_var.html'>$PATH Definition</a>
<br />
<a href='https://stackoverflow.com/questions/8288297/whats-the-relationship-between-environments-and-projects-in-virtualenvwrapper'>
Difference Between Projects and Environments in Virtualenvwrapper</a>
<br />
<a href='https://stackoverflow.com/questions/23997403/installed-virtualenv-and-virtualenvwrapper-python-says-no-module-named-virtuale'>
Setting VIRTUALENVWRAPPER_PYTHON Variable</a>
<br />
<a href='http://docs.python-guide.org/en/latest/dev/virtualenvs/'>Python Virtualenvs</a>
<br />
<a href='http://docs.python-guide.org/en/latest/starting/install3/osx/'>Installing Python 3 on Mac OS X</a>
<br />
<a href='https://stackoverflow.com/questions/6401951/using-different-versions-of-python-with-virtualenvwrapper'>
Another Way to set VIRTUALENVWRAPPER_PYTHON Variable</a>
