---
layout: page
title: Jekyll
permalink: /jekyll/
---

In the early days of the Internet, web sites were manually crafted relying on humans to laboriously type out HTML code. People started looking for a more efficient way to do this, and by the early 2000s, websites were mostly transitioning to storing the bits that changed (text on pages) in a relational database store. While it had some issues, this was the predominate method of creating websites until more recently.

Earlier in this decade, namely as a method to deal with how good hackers were getting, people began to develop a class of website tools to statically generate websites. While these systems are a bit closer to the metal (it requires a bit more interaction with command line tools) the benefit is that you close off an entire class of really frightening attacks that not only affect your sever, but the protection of the information for companies.

I'm introducing you to [Jekyll](https://jekyllrb.com), which is a "blog aware, static site generator." Once more, it's supported by [Github Pages](https://pages.github.com), so you can host your site there and take advantage of their infrastructure (e.g. you don't have to set up your own web hosting). There are other options if you need to run this in some other way, just come talk to me and I can blow your mind.

## Setting Up

Jekyll is a Ruby gem (remember from the install fest) that includes a bunch of tools to make it really easy to create entire websites. The first thing to do is check to everything is installed properly. We can do this by checking the version of the `gem` application that is installed by launching the terminal and typing `gem -v` and `npm -v`. You should see something like the following:

```
$ gem -v
2.5.1
$ npm -v
3.8.3
```

If you get an error, go back to the [Setting Up](/setting-up/) tutorial.

## Installation

This is pretty straight forward:

```
$ gem install jekyll
```

This can take a bit as it goes out to the [RubyGems](https://rubygems.org) website and figures out what other software you need to ensure this software works.

Once everything is finished, you can verify it was installed properly by checking the version:

```
$ jekyll -v
jekyll 3.1.3
```

## Quick Start

Now that we have everything we need to get rolling, let's create a new Jekyll project in the terminal:

```
$ mkdir -p ~/projects/ && cd ~/projects
$ jekyll new my-site
$ cd my-site
$ ls -lah
```

That's a lot of files! But let's test the system to make sure everything you need is working. To do this, we need to set up a web server that can compile the templates in to HTML code. Fortunately there's a utility included in Jekyll to do this easily:

```
$ jekyll serve
```

Now if you point your browser at [http://localhost:4000](http://localhost:4000), you should see a generated web page.

![default jekyll page](../images/web_page.png)

To stop the built-in server, simply hit `ctrl + c`.

## Folder Directory Overview

This is just an overview of the system, but if you want to view more information, check out the documentation on the [Directory Structure](http://jekyllrb.com/docs/structure/).

### _config.yml

This is where the settings for the site are stored. You will want to check out this file and see what's in there. As with all of Jekyll, it uses the [YAML](http://yaml.org/).

### _includes

This is where reusable blocks of code go. You may hear them referred to as "partials" or "slices", but this is really just blocks of code that you can **include** in your layouts and pages.

### _layouts

This is where templates that handle the layout of your site. Think of this as a wrapper for bits of HTML that don't change on your pages.

### _posts

This directory includes all the posts for your site. There is not a database, every post is its own file.

### _sass

We'll get in to this in a separate session, but this is where we put our CSS (actually SCSS) that is compiled on the site.

### css

You won't typically edit files in this directory, but the main **SCSS** file that tells SASS how to compose the stylesheets lives here.

### _site

When you statically build a website, it ends up in this directory.

### about.md

This is a static page that is included. Note the `yaml` **header** at the top of the page:

```
---
layout: page
title: About
permalink: /about/
---
```

This tells jekyll which **layout** to use, the **title** of the web page, and a **permalink** (the URL after the domain name) for the page.

### feed.xml

This is the file that generates the site feed for RSS readers.

### index.html

This is the landing page for the site.

## Creating Pages

Creating pages in Jekyll just requires that you create a new file in the project directory that is either a Markdown or HTML file (with a `.md` or `.html` extension).

Open atom and create a new file in the `my-sites` directory of `cv.md` and add the following:

```
---
layout: page
title: Curriculum Vitae
permalink: /cv/
---

This is my CV written in markdown.

It doesn't make my eyes bleed as much as HTML, and I can do ordered lists like this:

* item 1
* item 2

[links like this](https://www.clir.org)

and images with ![alt title](https://i.imgur.com/8sqExKf.gifv)

```

## New Posts

Posts live in the `_posts` directory and have this naming convention:

```
YYYY-MM-DD-my-title-is-called-this.md
```

I'll create a new file in atom and save it as `_posts/2016-04-19-teaching-jekyll.md`

In that file, I'll add the following header information:

{% highlight markdown %}

---
layout: post
title: "Teaching Jekyll"
date: "2016-04-19 10:40:36 -0400"
---

Jekyll is a lot of fun!
{% endhighlight %}

If you reload your web browser, you should now see the new post added:

![jekyll new post](../images/first_post.png)


## Deploying

When we did the [Introduction to Github Pages](/github-pages/), we created a specially named repository that would serve the HTML contents of your repository. There's another trick that if you have a repository with a special branch (`gh-pages`), you can get to that project at

```
https://your-user-name.github.io/project-name
```

Create a new project on github and follow the directions for creating a repository with existing code. Once finished, create the `gh-pages` branch in your project:

```
$ git checkout -b gh-pages
Switched to a new branch 'gh-pages'
```

Add all the project files to your git repository:

```
$ git add .
```

And commit them:

```
$ git commit -m "Added new jekyll files"
```

Now push to github:

```
$ git push
```

After a few minutes, you should be able to visit the page at https://your-user-name.github.io/my-site (where you replace 'your-user-name' with your actual Github username).
