---
layout: page
title: Introducing HTML5
permalink: /html5/
---

Modern web pages are complex systems that can be broken down in to three major components: **Structure**, **Presentation**, and **Interactivity**. The structure of a web page is represented in the **H**yper**t**ext **M**arkup **L**anguage (HTML), the presentation in **C**ascading **S**tyle**s**eets, and interactivity *mostly* with JavaScript. Dealing with these different components (along with variations in browsers and operating systems) has been an issue since the beginning of the Information Age. Eventually we'll start taking some shortcuts, but for now, we'll do this the old fashioned way, where we walk up-hill both ways in the snow.

## Basic HTML Structure

{% highlight html %}
<!DOCTYPE html>
<html>
<head>
</head>
<body>
</body>
</html>
{% endhighlight %}

## Tags
{% highlight html %}
<tagname>My Content</tagname>
{% endhighlight %}

## Tag Attributes
{% highlight html %}
<tagname id="content" class="orange">My Content</tagname>
{% endhighlight %}

## Useful tags

{% highlight html %}
<div>This is a page division</div>
<section>This is a page section</section>
<h1>This is a header, and you can do up to h6</h1>
<p>This is a paragraph</p>
<a href="http://clir.org">link to clir.org</a>
<img src="http://s.quickmeme.com/img/78/7896cefbd0a3e17496212592ad6e1a8fe913fc3cfdf4586867e9cf2517ad4942.jpg">
<strong>This is strong text</strong>
<em>This is emphasized text</em>

<ul>
    <li>Unordered list</li>
</ul>

<ol>
    <li>Ordered list</li>
</ol>
{% endhighlight %}

## CSS

CSS uses **selectors** for telling the browser which **tags** to apply a given style to.

{% highlight css %}
strong {
    color: red;
}
{% endhighlight %}

Applying this stylesheet to a page will cause anything between the `strong` elements to display in red.

You may also need to be more specific in which element you want to apply a style to. Take the following:

{% highlight html %}
<p class="key" id="first">CLIR is a great organization</p>
<p class="html" id="second">Wayne says crazy stuff that makes no sense.</p>
{% endhighlight %}

We can do something like this to visually represent the important information on the page:

{% highlight css %}
#first {
    color: red;
}

#second {
    color: blue;
}

.key {
    font-size: 36px;
}

.html {
    font-size: 12px;
    font-family: sans-serif;
}
{% endhighlight %}

## Basic Template

{% highlight html %}
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8">
    <meta http-equiv="x-ua-compatible" content="ie=edge">
    <title>Your Title Here</title>
    <meta name="description" content="">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <style>
        // Styles go here
    </style>
</head>
<body>
    <!-- Add your site content here -->
    <p>Hello World.</p>
</body>
</html>
{% endhighlight %}

## Recap

These are the very (*very*) basics of HTML and CSS, the building blocks of all websites. As we progress through the weeks, we'll be getting more sophisticated with how web pages are constructed (including working with mobile devices), deploying to servers, and toolchains to make working with these blocks less of a pain.
