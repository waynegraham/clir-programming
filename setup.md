---
layout: page
title: Setting Up
permalink: /setting-up/
---

# Installing

This will *hopefully* be a good script for walking people through the installation process on Windows and OS X for the exercises in the coming weeks.

* [Windows Instructions](#windows)
* [OS X Instructions](#os-x)

Everyone will need an account at [GitHub](https://github.com).

# Windows

## Phase I: Rails Installer

Go to [RailsInstaller](http://railsinstaller.org/en) and download the the [Windows Ruby 2.2](https://s3.amazonaws.com/railsinstaller/Windows/railsinstaller-3.2.0.exe) version (or click on the link).

Launch the install wizard and click **Next** at each step to accept the defaults.

#### Be sure to check the boxes for *Install git (recommended)* and *Add executables for Ruby, DevKit (if checked above) to the PATH*

![path settings](http://installfest.railsbridge.org/installfest/img/WinRailsInstaller.jpg)

## Phase II: SSH and git

At the end of the installer there will be a checkbox asking 'configure your git and ssh environment'. **Leave this box checked**. It will open a terminal window that you need to **type into**.

When it asks Please enter your name, for example mine is: Wayne E. Seguin

Type your actual full name into the console and press **[enter]**

When it asks Please enter your email address, for example mine is: wayneeseguin@gmail.com

Type your actual email address into the console and press **[enter]**

<div class="warning">
Use the same email address for heroku, git, github, and ssh.
</div>

### Update Git

The version of Git that comes with RailsInstaller is old, so we will be updating that next.

Go to [http://git-scm.com](http://git-scm.com) and download the installer. You want version 2.7.2 or newer.

Run the installer, and it will ask you where you want to install it. Change it **FROM** C:\Program Files\Git **TO**, C:\RailsInstaller\Git like the picture below.

![git setup screenshot](http://installfest.railsbridge.org/installfest/img/directory.png)

It will warn you that the directory already exists. Click yes to install to that folder anyway.

Click next twice, and select, **Use Git from the Windows Command Prompt**.

![git setup screenshot](http://installfest.railsbridge.org/installfest/img/command.png)

For all command-line exercises use the `git bash` prompt. It will save a lot of headaches. You may want to pin it to the taskbar:

![pin prompt](http://installfest.railsbridge.org/installfest/img/railsbridge_windowsScreenshot-commandprompt-pinnedtotaskbar.png)

### Phase III: Text Editor

We'll use [Atom](https://atom.io/) as our text editor. As we get more in to this, we may switch to [vim](https://github.com/vim/vim#what-is-vim), but the learning curve is significantly higher.


# OS X

## Phase I: Learn your Mac OS X Version

* Click on the Apple icon in the top left of your screen.
* Select "About This Mac"
* In the window that comes up, under the title "Mac OS X" there will be a version number.
  * If it starts with 10.11, you have **El Capitan**.
  * If it starts with 10.10, you have **Yosemite**.
  * If it starts with 10.9, you have **Mavericks**.
  * If you have anything else, we need to talk...
* Write down the Mac OS X version you have.

## Phase II: Package Managers

#### Step 1: Terminal
* Look for Terminal.app inside Applications -> Utilities, or use Spotlight search (Command + Space Bar) to find it.

Add it to your dock; you'll be using it a lot. (To add it to the dock, click and hold the dock icon once Terminal is open. Select options -> keep in dock.)

<div class="info">
Arrange your windows so that Terminal and your web browser are next to each other. You will want to read from your browser and type into your terminal at the same time.
</div>

#### Step 2: Install a Compiler

Xcode Command Line Tools include lots of tools your computer needs to set up new software.

Verify if you have a compiler installed. In the terminal, type this:

```
$ gcc --version
```

You should have something along these lines:

> Configured with: --prefix=/Applications/Xcode.app/Contents/Developer/usr --with-gxx-include-dir=/usr/include/c++/4.2.1
> Apple LLVM version 7.0.2 (clang-700.1.81)
> Target: x86_64-apple-darwin15.3.0
> Thread model: posix

If you don't see something like this, run this command in the terminal:

```
$ xcode-select --install
```

#### Step 3: Install Homebrew

Homebrew is a package manager for OS X and allows you to install software without having to do a Google search to find things. This significantly speeds up installing software.

```
$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

Now you can install the necessary tools:

```
$ brew install git gpg
```

Now to verify the versions:

```
$ git --version
git version 2.7.2
$ brew -v
Homebrew 0.9.5 (git revision ae41d; last commit 2016-02-29)
```

#### Step 4: Install RVM

RVM stands for Ruby Version Manager and is the easiest way to install and manage Ruby. The [official RVM install instructions](https://rvm.io/rvm/install) are available here, but this should work for you:

```
$ gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
$ \curl -sSL https://get.rvm.io | bash -s stable
```

#### Step 5: Configure RVM to use Homebrew

Type this in the terminal:

    $ rvm autolibs homebrew

#### Step 6: Install Ruby

Type this in the terminal:

    $ rvm install 2.3.0

This downloads and compiles Ruby, which takes a while.

When it's finished, type this in the terminal:

    $ rvm use 2.3.0
    $ rvm --default use 2.3.0

Now you can verify the version with this in the terminal:

    $ ruby -v
    ruby 2.3.0p0 (2015-12-25 revision 53290) [x86_64-darwin15]

### Phase III: Text Editor

We'll use [Atom](https://atom.io/) as our text editor. As we get more in to this, we may switch to [vim](https://github.com/vim/vim#what-is-vim), but the learning curve is significantly higher.

### Phase IV: Better Terminal

Install [iTerm2](https://www.iterm2.com/). If you want to get really fancy, you can use `brew cask` to install this:

```
$ brew cask install iterm2
```

> **Note**: If you previously installed Hombrew-Cask, you will need to run this command to update: `brew uninstall --force brew-cask; brew update`

### Phase V: Extra Credit

Make your bash prompt look soooooo much better with `bash-it`:

```
$ git clone --depth=1 https://github.com/Bash-it/bash-it.git ~/.bash_it
$ ~/.bash_it/install.sh
```

Close `Terminal.app`/`iTerm2` and reopen.

### Phase VI: SSH Keys

Passwords are the worst. Let's not use them, but instead a far better method of secure communication with SSH keys.

```
$ ssh-keygen
```
