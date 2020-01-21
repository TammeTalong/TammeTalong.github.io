---
layout: post
title:  "My thoughts on SCSS and SSG"
author: Samuel Meijer
date:   2019-11-15 08:25:30 +0100
categories: jekyll update
comments: true
---
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Mauris eleifend, felis a luctus luctus, velit purus aliquam diam, a facilisis nunc lorem et turpis. Praesent imperdiet quam a sem scelerisque, sit amet tempus arcu iaculis. Aliquam sollicitudin felis tortor, nec porta justo malesuada eu. 

### Pre-compiling CSS
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Mauris eleifend, felis a luctus luctus, velit purus aliquam diam, a facilisis nunc lorem et turpis. Praesent imperdiet quam a sem scelerisque, sit amet tempus arcu iaculis. Aliquam sollicitudin felis tortor, nec porta justo malesuada eu. Mauris semper ornare nibh at tristique. Pellentesque aliquam a est vel consectetur. Donec lacinia ut est eget tristique. Ut in ipsum tempus odio pellentesque rutrum. In a cursus nulla. Ut ut commodo lorem, eget suscipit lectus. Nam a libero luctus, rhoncus nulla ac, pretium ante. Donec at felis et metus semper lacinia. Proin lobortis arcu nec egestas aliquet.

### Static Site Generators (SSG)
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Mauris eleifend, felis a luctus luctus, velit purus aliquam diam, a facilisis nunc lorem et turpis. Praesent imperdiet quam a sem scelerisque, sit amet tempus arcu iaculis. Aliquam sollicitudin felis tortor, nec porta justo malesuada eu. Mauris semper ornare nibh at tristique. Pellentesque aliquam a est vel consectetur. Donec lacinia ut est eget tristique. Ut in ipsum tempus odio pellentesque rutrum. In a cursus nulla. Ut ut commodo lorem, eget suscipit lectus. Nam a libero luctus, rhoncus nulla ac, pretium ante. Donec at felis et metus semper lacinia. Proin lobortis arcu nec egestas aliquet.

### Robots.txt
Robots.txt is used to give instructions to web robots. It can be configured for specific web robots or contain general instructions for all of them. The main functionality of robots.txt is to allow or disallow access to certain parts of your webpage when the robot crawls through it.  
The instructions are both public and advisory, meaning that the robots can chose to ignore your instructions. 
This means that the instructions in robots.txt should not be seen as a security measure for the webpage.

To configure robots.txt you specify the robot you want to give instructions to by defining a "User-Agent". If the user-agent is defined with "*" it means the instructions are general and applies to all of the robots visiting your webpage.  
By using "Disallow: RELATIVE-URL" you can specify which parts of your webpage you wish the robot to ignore, or simply write "/" as the relative-url to disallow all of the content. By paring "Disallow:" with an "Allow:"-instruction you can allow access to parts of the content you wish the robot to ignore.  
Its also very common to add a reference to the webpage sitemap in robots.txt.  

{% highlight ruby %}
<meta name="ROBOTS" content="NOINDEX, NOFOLLOW">
{% endhighlight %}
A `<meta>`-tag can also be included in the webpages `<head>`-element with information to visiting robots if the webpage wishes for the robot to index the page and search for links to follow or not.

Since this webpage is only meant to be used for school assignments and there is no value for external parties to be able to find or access the webpage its robots.txt is set to disallow robots access to all of its content.

### Humans.txt
Humans.txt is used to describe the persons that has contributed to the development of the webpage.  
It can include any chosen information, but usually includes information about the persons name, which part of the development they were involved in and some kind of contact information.  

Sometimes humans.txt also includes a section with technical information about the webpage. Usually this section contains information about the tools that were used in the development, the last time the content of the webpage was updated and similiar technical information.

A section for extended thanks to persons or companies are also included by some.

{% highlight ruby %}
<link rel="author" href="humans.txt">
{% endhighlight %}
A `<link>`-tag can also be included in the webpages `<head>`-element with a reference to the humans.txt file.

### Disqus
This webpage uses the free service _Disqus_ to implement the ability to leave comments on blogposts. I chose to use Disqus because it is a well known and free alternative while also being easy to implement. 

First you have to register an account at [_Disqus_](https://disqus.com) and link your webpage to your account. The second thing you have to do is add a predefined code snippet into your layout. The code you get from Disqus evaluates if the _YAML Front Matter_ of the currently active page has a property called _comments_ set to _true_, and if it does it adds a `<div>`-element containing the Disqus comment field to the page.

I implemented the code snippet from Disqus by adding a html-file in the _includes folder with the predefined code. I then included that file at the bottom of the page in the layout for blogpost, while adding the property `comments: true` to the front matter of the blogposts where I wish to include the ability to comment.

### Open Graph
Open graph is used to enable your webpage to turn into an open graph-object, which means you can decide which information to show when a user shares the webpage url on a social media.  

To configure the open graph-object you add `<meta>`-tags to your webpage `<head>`-element, one for each property.  
There are four required properties, these are: _Title, Type, Image, URL_.  
There are several other optional properties that can also be included to further add information about your webpage or the page that is currently being shared.

{% highlight ruby %}
<meta property="og:title" content="The title to use">
{% endhighlight %}
The _title_-property descripes the title of the open graph-object and should generaly be the same as the title of your webpage or the title of the specific page that is being shared.

{% highlight ruby %}
<meta property="og:type" content="The type to use">
{% endhighlight %}
The _type_-property describes the type of the content. Some types require additional information added, for instance if the type is set to "video" or "audio" information about the duration should be added.
For this webpage the type is set to "webpage" and therefor does not require any additional information. 

{% highlight ruby %}
<meta property="og:image" content="Address to the image to use">
{% endhighlight %}
The _image_-property consists of a link to an image to show and represent your open graph-object. Several optional properties can be added to configure the image, for instance can the width and height be set to a fixed number of pixels or an alternative text to describe the image can be added.

{% highlight ruby %}
<meta property="og:url" content="The absolute URL">
{% endhighlight %}
The _url_-property is the absolute url to your webpage or the specific page that is being shared. This is used as the objects ID.