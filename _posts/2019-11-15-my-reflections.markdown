---
layout: post
title:  "My thoughts and reflections"
author: Samuel Meijer
date:   2019-11-15 08:25:30 +0100
comments: true
---
This is a short summary of my thoughts and reflections on the tools and methods used in the development of this webpage.

### Pre-compiling CSS
A _CSS_ preprocessor is used to add  extra features in the development process of a webpage by extending the functionality of regular _CSS_. This webpage used the _CSS_ preprocessor called [_SASS_](https://sass-lang.com) during its development.

Using _SASS_ enables the ability to use _Variables, Nesting, Partials/Import, Mixins, Extend/Inheritance_ aswell as calculations with _Arithmetic Operators_ while writing _CSS_. Because of this I found using _SASS_ to be more similar to coding in _JavaScript_ than when writing regular _CSS_, and therefor removed alot of the repetitiveness that can occur when writing regular _CSS_. Since the design of this webpage is a modefied version of the _Jekyll_-theme called _Minima_, that already contains alot of _CSS_ written with _SASS_, all of the extra functionality mentioned above has been used. 

_Variables_ are perfect to use for values that will be repeated alot, for instance the size and color of text. By using a variable to define a desired value it gives the possibility to change a single value in one place while still affecting several different elements on various sections of your webpage, hence leading to less need for repetition aswell as easier maintenance.

_Nesting_ refers to the ability to write _CSS_ for several elements that are children of a specific element or class at the same time, leading to less need for repetition aswell as better structuring than when writing regular _CSS_.

_Partials/Import_ refers to the ability to write CSS in several different files that can be linked to each other, very similar to modules in _JavaScript_. This makes it easier to separate styling with different purposes from each other, and therefore makes it easier to manage your styling. As an example the styling during the development of this webpage was structured to separate the basic styling done to elements from the styling done for layout purposes, aswell as keeping all of the variables in a separate file.

_Mixins_ are very similar to functions in programming languages, which can be usefull when applying a value to several settings at once or calculate a new value from a given value. In this webpage _Mixins_ has been used primarily to set font sizes relative to a given "standard size" that is defined by a variable. Correct use of _Mixins_ is one of the best and most used tools to combat repetitiveness when writing _CSS_ with a preprocessor.

_Extend/Inheritance_ is used to make a _CSS_-class inherit settings from another _CSS_-class. This is done to prevent the need to use several _CSS_-classes on a single element, and can also be used to prevent repetition of styling if two or more _CSS_-classes share several settings with each other. On this webpage _Extend/Inheritance_ was mainly used on classes that act as "Wrappers" and share several similar settings while still having a few settings that separate them from each other.

_Arithmetic Operators_ gives the ability to performe calculations while styling with _CSS_. This is very useful when combined with _Variables_ and _Mixins_, and it is with these features that _Arithmetic Operators_ has been used in the development of this webpage.

#### Pre-compiling CSS - Cons
While _CSS_ preprocessors adds alot of extra functionality and features, they also come with some possible cons you have to take into consideration.  

First and foremost, the styling you write with a _CSS_ preprocessors has to be compiled into "regular" _CSS_ before it can be applied to a webpage. The most obvious drawback of this is that more tools are needed than if you write regular _CSS_, both for the preprocessor aswell as the compiler, hence adding more complexity and the possibility for bugs associated with the tools. Another drawback is that debugging gets harder as the line numbers in the compiled _CSS_-file does not match the line numbers of the files that is used in the preprocessor. A possible solution to that specific problem is using so called _Source Maps_.  

Another problem that occurs when working in a team is that each and every member has to use to same tools and methods while working on the project.  

One thing I personally felt while working with this webpage is that it is easy to use features just because they are available, even if they are not really needed. It is also very easy to overuse some features, such as nesting, making it possibly worse to manage than if done with regular _CSS_.  

A possible drawback with this specific webpage is that I think there are probably quite a bit of styling that is no longer used or needed, since the design of this webpage is a modefied version of a _Jekyll_-theme. One of the reasons why I chose not to go through and test each of the styling settings is the fact that it is split into several files with quite a bit of _Mixins_, _Variables_ and _Extend/Inheritance_. This makes it very timeconsuming to go through and test all of the styling that is not directly written by me, since a minor change somewhere can have a major impact on a not so obvious part.

### Static Site Generators (SSG)
A static site generator(_SSG_) is used to generate a static webpage from a collection of sourcefiles. This webpage uses the _SSG_ called [_Jekyll_](https://jekyllrb.com) in its development. I had zero experience with using a _SSG_ before this webpage and I have to admit that my first impression was that it felt a little advanced and complicated when compared to regular development without _SSG:s_. After a couple of hours of reading and testing I instead appricieated much of the possibilites that a _SSG_ enables.

The ability to use _Partials/Includes_ in combination with the ability to define different _layouts_ makes it easy to customize your webpage and its different sections without repetitve coding. This means that for example the `<header>` and `<footer>`-elements only has to be written once and can be included in every page by linking instead of having to be rewritten for every single page.

The abbility to use _variables, loops_ and _evaluation_ means that its easy to customize the content and get the desired functionality or look for your specific content. Another added possibility with _Jekyll_ is the ability to write the textcontent in _Markdown_ instead of directly in the HTML-files.  
These things in combination with _Partials/Includes_ makes the development time considerably lower, once you get the hang of it, while also allowing easier maintenance after launch. 

Other added benefits of a static webpage is the fact that they are both faster and more secure than dynamic webpages, since there is no database or userinput that has to be handeld by the server or can be compromised by ill-willing individuals.

Since a _SSG_ follow the principle of "what you see is what you get", using one is suitable for projects that does not require any dynamic information such as user input or realtime database communication.
Perfect examples for suitable projects are blogs, like this one, or webpages where the desired functionality is to present static information, for instance a webpage for a small sports club.  
If the webpage requires any dynamic information a _SSG_ should not be used.

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