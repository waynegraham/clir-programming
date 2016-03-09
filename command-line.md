---
layout: page
title: Introducing the Command Line Interface
permalink: /command-line/
javascript:
  - /js/hint.js
---

# Command Line Interface (CLI)

The transition to interacting with your computer on the command line interface can be a little jarring at first if you're accustomed to working in an environment dominated by windows, cursors, buttons, and other [GUI](https://en.wikipedia.org/wiki/Graphical_user_interface) pleasantries. Really, though, these graphical features are often just façades for functionality that can be achieved with more flexibility and speed by typing commands directly into a terminal.

Getting comfy on the command line is a bit like learning to drive a stick shift. At first, it can seem sort of ridiculous and obtuse. If automatic transmissions exist, what's the point? Over time, though, you start to realize that the manual transmission gives you a more complete and robust level of control over the car. Instead of coaxing the car to do what you want, you order it. This is exhilarating, and you begin to realize that the stick shift solves a set of problems and annoyances that, in the past, you didn't even know you had.

This tutorial references a shell application called [**bash**](https://en.wikipedia.org/wiki/Bash_(Unix_shell)), which is the default on OS X and ubiquitous on unix-based platforms. If you're using **OS X**, click on the magnifying glass at the top right of the screen, type "**Terminal**," and press Enter (or **⌘ + space**). For Windows users, open the *Git Bash** prompt.

> *Note:* The bash shell is just one shell application that runs on modern systems. Other popular modern shells include [zsh](http://www.zsh.org/) and [tcsh](https://en.wikipedia.org/wiki/Tcsh). If you're 'old skool', you may also remember (Thompson) shell, bourne, and c shell.

# pwd

First, type `pwd`. (Here and throughout the rest of the tutorial, always ignore trailing punctuation when commands are given inline, and never type the `$`). This stands for "**print working directory**." This command just tells you where you are in the file path. When you hit enter, you should see something like "`/Users/yourusername`" (OS X) or "`C:\Users\username`" (Windows). This means that you've started out in the home directory for your user account. Think of pwd as a way to get your bearings. When I sit down at a terminal, this is usually the first thing I type.

# ls

Now that we know where we are on the computer, the next thing you'll usually want to know is what's in the current directory - what are the files and folders that are accessible at this location on the system path? To see, type `ls` , which stands for "list". This just outputs the contents of the current directory.

Depending on your setup (and how many files you have set up), you will see something like:

If your setup is like mine, you should see three folders - "`Desktop`," "`projects`," and "`public_html`."

# cd

Ok, now we can see (a) where we are and (b) what stuff exists in the current directory. But you'll never be in a situation where all your work is in a single directory, so a really important piece of the puzzle is the `cd` command, which stands for **change directory**. This does what you'd expect. Think of it as using Windows Explorer or Mac Finder to move around to different folders on your computer. Say we want to change into one of the directories that exists inside of your home user directory. You can do that by typing `cd`, space, and then the name of the directory. Go ahead and change into the "Desktop" directory with `cd Desktop`.

Now, type the `ls` command again to see the contents of the new directory. If changed directories successfully, you should see all the files and directories on your `Desktop`. Now, let's go back to your user directory. To move "upwards" on the filepath, type `cd ..`. The double period "`..`" stands for going up a single directory level. So, if you wanted to go up two levels, you'd type `cd ../..`. Three, `cd ../../..`. Etc.

So, after typing `cd ..` , you should be back in your home user directory where you started.

# First Quiz

How do you know you're in the directory where you started?

# mkdir

Say you want to create a new directory ("folder" in Windows parlance). I put all of my work in a folder called "`projects`." Go ahead and create a new folder called projects by typing `mkdir projects`. "**mkdir**" stands for "**make directory**". It just creates a new folder with nothing inside of it.

Once you type `mkdir projects`, type ls again to confirm that the folder was created. Then change into the new folder with `cd projects`. Once you're in the new folder, go ahead and create another subdirectory inside of projects called whatever you want - say, `mkdir testdir`. Then, change into the new `testdir` directory with `cd testdir`.

# touch

`mkdir` creates directories, but directories are just buckets for actual data, which is contained in files. To create a new file in the current directory, use the `touch` command. Type `touch textfile.txt`. This will create a blank text file called `textfile.txt`. I often tend to type `ls` or `pwd` before or after important commands just to make sure that I'm in the right location and that the previous command did what I wanted it to.

Now, create three more textfiles like this -

`touch {textfile2.txt,textfile3.txt,textfile4.txt}`

You can add as many new files as you want to the comma-delimited list to create a bunch of files with one command. Now, there should be 4 blank text files in the directory "testdir", which sits inside of the "projects" directory.

# Quiz time

How many files are in the `test` directory?

# cp

Say we have a file that we want to copy. In Finder/Explorer, you would do this by clicking on the file, then hitting `control` (er, `command`, or whatever) `+ c`, and then hitting `control + v` to paste it again. In **bash**, you can use the `cp` command. Let's copy "`textfile4.txt`" as a new file called "`copiedfile.txt`". Type `cp textfile4.txt copiedfile.txt`. Then type `ls`, and check to make sure that the copied file is there.

Often you want to copy entire directories. This is a little different. Type `cd ..` to change up to the projects directory, and then type `ls` to view the contents. There should just be the "`testdir`" directory. Imagine that you wanted to make a copy of that directory inside of another directory. Let's go ahead and create that second directory. Type `mkdir anotherdir`. Now, to copy "`testdir`" (and all of its files) into "`anotherdir`", type `cp -r testdir anotherdir/`. Now, change into another dir (`cd anotherdir`) and type `ls` to confirm that the folder was copied. The "`-r`" is called a **flag** - a lot of commands have optional functionality that can be specified with flags. In this case, the "`-r`" stands for **recursive**, which tells the `cp` utility to loop through and copy the contents of the directory.

## rm

Often, you need to delete files. In Explorer or Finder, "deleting" is kind of a misnomer - you "move things to the trash bin," etc. What that means, though, is that you can recover the file if you decide that you want it later. On the command line, though, delete means delete, no questions asked. Once a file (or a directory) has been removed, it is totally gone from the system and can never be recovered (short of some kind of insane hardware-level recovery, but even that's unlikely).

Whenever you use `rm`, just make sure you're dialed in and not doing something dopey. And make sure that the command is formed correctly; a mistake here could destroy massive swaths of your file system.

Are you getting the picture that this can lead to bad times if you're not careful?

Let's delete a single file. Change into the `testdir` directory that we just copied. There should be the four text files in there. To remove a single file, type `rm textfile1.txt`. Type ls to confirm that the file was deleted. Now, delete two files at once with `rm {textfile2.txt,textfile3.txt}`. Now, there should be just the last "`textfile4.txt`" file - confirm this with `ls`.

Now, the **scary part** - *deleting entire directories*. Change back up into the projects directory ( `cd ../..` ). Again, type ls just to make sure that you are where you think you are - there should be the original "`testdir`" and the "`anotherdir`", which contains the (now mangled) copy of "`testdir`". Delete "`anotherdir`" with this command - `rm -rf anotherdir/`.

Type `ls` - the directory should be gone. Here, the "`-rf`" flags are similar to the "`-r`" flag that we used with "`cp`" - it stands for "recursive force". In other words, wipe out everything in sight and don't ask me about it.

# Quiz time:

What could go wrong if you pass the recursive flag in the wrong directory?

# tar

Last, we'll cover an archiving utility called `tar`. This is a really old utility that stands for **Tape ARchive** (this is from when computers saved all data to tape drives) A `.tar` file is kind of like a `.zip` file (without any compression) - it's an archive that bundles together a lot of files or directories into a single unit. In this exercise, I won't spell out all of the traversal, listing, and add/removal commands that you'll need to use - see if you can figure them out.

Make sure you're in the projects directory, and do this:

1. Create a new directory.
2. Change into the new directory.
3. Create three blank text files. Try to do this with a single command.
4. Create a new subdirectory.
5. Move the three files into the subdirectory. Again, try to use just one command.

Now, we have a folder with three files in it. Let's create a `.tar` file called `anyname.tar` out of that folder with this command - `tar cvf anyname.tar dir/`, where the "`dir`" is the name of the directory that you created in step 4 above. Confirm that the file got created. The new file contains a copy of the directory. You can examine the contents of a tar file without unpacking it with the command `tar tvf anyname.tar`. This will list the files and folders in the `tar`.

Now do this:

1. Delete the original version of the directory with the three text files (careful here..).
2. Recreate the directory by unpacking the tar file with this command - `tar xvf anyname.tar`
3. List the directory contents to confirm that the directory was unpacked.

What do the little letters after the core tar command mean? These are a bit cryptic, and you just have to remember them. Like `rm` and `cp`, `tar` has lots of options that you can configure. The string of letters specifies a particular combination of behaviors that define the functionality that you're trying to achieve. For example, "xvf" stands for **eXpand, Verbose, and File** - which translates to:

> "I want to expand an existing tar file, as opposed to creating a new one. I want the tar utility to be "verbose" when it does its work, which means that it will print out information about what it's doing. Last, I want to use the file that I type at the end of this command as the source .tar file to unpack."


Imagine if poetry could be that condensed! Even closer readings, we would need to perform. This stuff is just syntax that you have to remember. I often have to check reference for commands like tar to make sure that I have the options right, so don't worry about learning everything. Google is always there.

Next, do this:

1. Delete the tar file that we created before.
2. Create a new tar file from the testing directory that contains the three text files. This time, though, use this variation on the command: `tar czvf anyname.tgz`

The difference here is that the added "`z`" in the options tells tar to use a utility called "`gzip`" to compress the tar file. This means that the total size of the file will be smaller than the sum of its parts as they exist normally on your computer. This is useful is you want to package up a lot of data - always better if the file is smaller.

Now:

1. Delete the directory with the text files so that the only thing in the current directory is the `.tgz` file that you just created.
2. Unpack the compressed tar with this command: `tar xzvf anyname.tgz`

`tar` is a really powerful and highly configurable utility - you can add files individually to a tar that already exists (but not one that's compressed...), unpack file individually, and lots of other stuff. Most of the commands that you'll use are really complex programs in their own right - but you don't have to have comprehensive knowledge of the full depth of the utilities to use them effectively and benefit from them.

Really, the best way to get comfy on the command line is just to bumble around on it for a month or so. Short of reckless use of `rm`, not a whole lot can go wrong.

# Getting Help

All of the switches and order for all the different commands (see [all the different commands](http://ss64.com/bash/) is a lot to remember. Fortunately the shell ships with all the documentation you need with the man (short for manual) utility. For any command, you can read the manual for the utility by simply typing `man` utility. For the commands we covered here, you can read the manuals with the following:

* `man pwd`
* `man ls`
* `man cd`
* `man mkdir`
* `man touch`
* `man cp`
* `man rm`
* `man vim`
* `man tar`
* `man man`

If you forget any syntax, you can quickly read through the manual (hit the space bar to page down) to see what flags and options you can pass any utility.


## OS Power Hint

(Sorry Windows users)

![Drag Folder](http://media.24ways.org/2013/coyier/drag-folder.gif){: .img-responsive}

# Exercises

## Listing Directories

Change to the `Desktop`. List all the directories on the `Desktop`.

{% highlight console %}
$ cd ~/Desktop
$ ls -d *
{% endhighlight %}

Change to the `Desktop`. List all files and directories, 1 per line.

{% highlight console %}
$ cd ~/Desktop
$ ls
{% endhighlight %}

## Making Directories

Create a directory named demo.

{% highlight console %}
$ mkdir demo
{% endhighlight %}

### Deep Directories

Change to the desktop. Create the following directory structure using one command: `demo/foo/bar/praxis`

{% highlight console %}
$ cd ~/Desktop
$ mkdir -p demo/foo/bar/clir
{% endhighlight %}

## Creating Files

Change to the `demo` directory. Create a file named `hello.txt` in the `demo` directory.

{% highlight console %}
$ cd ~/Desktop/demo
$ touch hello.txt
{% endhighlight %}

## Making, Moving, Deleting

Create a new directory called test_projects with three text files in it: `test_1`, `test_2`, `test_3`. Within `test_projects`, create another directory called `files`. Move the test files into the new directory. Move into the new directory to make sure it worked. Then delete the `test_projects` directory.

{% highlight console %}
$ mkdir test_projects
$ cd test_projects
$ touch test_1.txt
$ touch test_2.txt
$ touch test_3.txt
$ mkdir files
$ mv test_1.txt files
$ mv test_2.txt files
$ mv test_3.txt files
$ cd files
$ ls
$ cd ..
$ rm -rf test_projects
{% endhighlight %}

## Tarballs

Create a tarball of the `demo` directory

{% highlight console %}
$ tar -cvzf ~/Desktop/demo
{% endhighlight %}

## Getting Better

* [The Command Line Crash Course](http://cli.learncodethehardway.org/book/)
* [The Ultimate Tar Command Tutorial with 10 Practical Examples](http://www.thegeekstuff.com/2010/04/unix-tar-command-examples/)
