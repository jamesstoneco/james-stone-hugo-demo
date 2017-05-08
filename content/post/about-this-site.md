+++
date = "2017-05-06T19:43:41-07:00"
author = "James Stone"
title = "About this site"
weight = 4

+++

I have built several Middleman, Assemble.io, and Panini (similar to Assemble) sites in the past. Thinking about the project I wanted to try a popular static site gen in a language I was not as familiar with to give myself a challenge. I have heard great things about go and hugo and I know that many of the Netlify properties are using it as well.

I was hugely impressed with the ease of the installation of go and hugo via brew and its speed. It renders instantly. This is quite amazing especially compared to the very slow and complex installs of ruby and middleman and the fast (but not nearly as fast as hugo) rendering times and ease of installation of Node.js and Assemble.io. One disappointment was that there was no facility to render pages based on datasets. Everything must have a markdown file.

I had three main challenges setting up this simple demo site. 1) getting a 3rd party ZURB Foundation based theme to work with Netlify 2) setting up a page template that differed from the blog and 3) getting the navbar to show the active state with the built in menu.

In the first case, since I have had this issue in the past using Middleman. Netlify does not seem to (or at least I could not find documentation on how to adjust this setting) automatically install bower or node in subdirectories. My solution was to move the related bower and gulp build files to the root directory and modify the paths.

The second challenge was due to poor documentation. I searched everywhere for how I could set up a new template and then use that in a page. Since I could not find any, I just made a wild guess based on my experience with Middleman. I set layout = “page” in my frontmatter which associates with my page.html template that I created and it worked. If this guess had not worked, I would have likely started digging into the hugo source to try to identify how it is loading templates and by which logic.

The third challenge was also due to poor or incomplete documentation. Like the example above, I believe that many static site generators make an assumption that you already have worked with other SSGs and sometimes that leads to missing information. Sometimes this can just be that the community understands a general way of working but hasn’t updated the documentation to reflect this. The theme that I started from added an “active” state / css class to the home page using an IsHome function, but did not do the same for other menu items.

So I set out to correct this. The first example I came across was this menu-functions page on the official hugo docs. This didn’t seem to work, and so I tried to isolate the objects and functions by outputing it directly to the screen {{ .Sites.Menus.navbar }} Unlike Assemble and Handlebars which give a full representation of the object, I got an ID, which ended up being less useful. The functions outputted nothing, which I assumed was a false indicator.

I did a bit more digging and found lots of other people confused about the same thing. I found an extensive article. I went through one-by -one and tried the different examples. In this article I found the missing bit of information that allowed me to get the menus to function properly. Bryanjeal posted a complete set including the frontmatter including [menu.main] identifier = “contact-us” Once I set this properly in my individual pages everything worked as expected. The issue that I have now is that there are errors throw by hugo which prevent the deploy from triggering. Reading his update this has to do with a naming convention of using about.html vs. about/index.html. Updating the naming convention corrects the error and allows the built to function correctly. This was not intuitive nor easy to deduct.

But this was not the end and I ran into errors with pages rendering properly and although it worked great locally and would build on Netlify, I got inconsistencies in my output.

So I took a look at another theme called bootie-docs that seemed to have the functionality that I wanted. I was able to extrapolate out how to set the active state based on the .URL in the menu being compared to the .URL of the page. With this new approach things seem to be sorted. However, I am not sure what is the best practice or best approach for building out this kind of functionality in general.

 - Site: https://james-stone-hugo-demo.netlify.com
 - Repo: https://github.com/jamesstoneco/james-stone-hugo-demo
