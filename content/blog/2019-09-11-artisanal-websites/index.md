+++
title = "An Artisanal Guide to Building Websites"
description = "Sclupting a web domain with your hands, a couple useful tools, and fostering an endless font of inspiration."
aliases = ["2018/11/04/optional-arguments/"]
layout = "blog/single.html"
[taxonomies]
tags = [
  "Web",
  "Tutorials",
]
[extra]
image = "cover.jpg"
image-credit = "Andrew Neel; @andrewtneel on Unsplash"
+++

I don't make my website to be fancy, I make it because it's fun! In order to share the fun, let's talk about how you can make your own!

The process of creating a website starts with a spark of inspiration, and can flow easily into a development environment using nothing more than your web browser and your favorite text editor. Often, having a couple more tools is useful, so we'll talk about them too. With an environment set up, we'll explore how all the pieces fit together, and learn some best practices to help keep things clean. We'll talk about how to publish your site painlessly and for free, then how to optionally get a domain and hook the pieces together.

In the end, you'll find yourself with a warm, friendly website you can hack on from nearly any machine (Windows, Mac, or Linux!). It's my greatest hope that you'll continue to craft something amazing, harnessing of the passion and creativity stirring inside of you.

This guide intended to suitable for all skill levels, has no hard system requirements, and should be suitable for all ages and backgrounds provided you can read and write english. It's preferable that you can trusted with a computer, and I really do recommend learning this with someone else, having someone to talk to about what you're learning is really useful!

If you find it inaccessible, or are willing to show off what you make, I'd love to hear from you, email me at operator@hoverbear.org. :)

<!-- more -->

## The Steps

To be more concrete, this guide will:

* Talk a bit about what might spark you to want to do this. ([The Why](#the-spark))
* Talk a bit about how the internet, websites, and this whole 'web development' thing works. ([The Stage](#the-stage))
* Get you acquainted with some power tools: Firefox Developer Edition, Visual Studio Code, your local terminal, your package manager, and Zola. [The Power Tools](#the-power-tools))
* Guide you through setting up a new project, how to start a preview server, and how to load it in your browser. ([The Project](#the-project))
* Take a brief interlude to introduce some core website concepts like `index.html` and URLs, giving you lots of links to learn more. ([The Core Cncepts](#the-core-concepts))
* Encourage you to learn some techniques and strategies for creating your site, and provide problems you can try to solve with them.
* Take a look at Github, and the Git version control tool, teaching you just enough to update your site and fix any stumbling blocks.
* Guide you through setting up a friendly robot to rebuild your site each time you change it.
* Guide you through wiring everything together so that you can access `your_username.github.io` from any computer on the planet, and see your website.
* Explore how to get a domain name so you can use `anything.dev` or some other address.
* Finally, close with some resources to keep you learning.

## The Spark

The best explorations start with a **spark of inspiration**, a **thirst for knowledge**, and a **boldness to learn** something new. In order to increase your chances of success in this new adventure, let's talk some reasons why you might want to build a website, and what you could use it for.

The wild rush of the early internet, starting at least for me in the decade of 1990, brought with it the unique concept of universally accessible content that anyone could create, with a bit of resources. I got really lucky, when I first was growing up the internet had only recently become popularized. We got to make websites in middle school by using an early File transfer Protocol client to send files to the server we had running in one of the  many closets around the school, and seeing my little web page up there on the big wide internet.

It was empowering. It could have become anything I wanted it to be. It was simple, just some text jotted down in whatever editor you had available, and then you used whatever browser floppy disc (yes, really!) you'd managed to find in the magazine isle of your local drug store (really!) and you could create anything you could imagine. Well, at least in theory.

Today, despite the task seeming monumental, the tools are even easier to access, and nearly limitless in power, and far easier to use. Using just the simple tools we'll talk about you can build things like blogs, image galleries, manuals, guides, animations, interactive storybooks, games, art pieces. These creations will be accessible on any device with an internet connection, from your phone, to your tablet, to your computer, even your TV or fridge (if it has a web browser, you can browse to your site!)

You can create anything you could imagine possible on an infinitely scalable blank sheet of nice, crisp paper and a box of fancy pens, stamps, and drawing gizmos, and a friendly robot who can move these tools around.

{{ figure(path="blank.jpg", alt="Start somewhere -- Kelly Sikkema; @kellysikkema on Unsplash", colocated=true) }}

If you're like me, right now, you really just want to build the biggest, coolest thing imaginable. Maybe it's a better version of your favorite game, or a more user friendly version of your least favorite mobile app. But these things are **super complex**, and while the task is not insurmountable, you should set small goalposts for yourself. It's the idea of working on **incremental, small changes** over time, and it's an important concept in engineering.

> Yes, you are doing is a form of engineering! What you're learning is a whole career path, you could get paid to do this!

Still, let's pick something useful! So let's use this time together to cover some of the things that almost every site has: A page talking about the purpose of the site (the 'about' page), and a journal (or 'blog') of news or thoughts. In essence, we'll make a simple version of the site you're reading this on.

You have the tools and ability to **learn whatever you want**, about anything.

## The Stage

The humble web browser. You can find them all over the place. Some are called Chrome, some are called Edge, others are called Safari, and my personal favorite is called Firefox. It doesn't really matter which one you use, they all do they same thing in the end. All that changes between them is *how they do it*.

When you open your browser and type in an address (like `hoverbear.org`) then hit return, you'll notice the browser goes ahead and replaces it with `https://hoverbear.org` while loading a really pretty picture and some text.

A lot is happening behind the scenes here! These things *are not important for understanding how to build your first website*, but they are **really freaking cool!** Let's take a really high level look:

1. Your browser takes `hoverbear.org` (the *domain*) and shows it to a *Domain Name Server (DNS)*.
    * Domains are purchased from *Registrars* and are *basically* unique. (Email me if you want to talk about that!)
    * DNS are typically run by your *internet service provider (ISP)* or other services like [Google Public DNS](https://developers.google.com/speed/public-dns/).
    * Usually your computer can discover one from your ISP, but you can also configure your own.
2. That Domain Name Server informs the browser of an *Internet Protocol (IP)* address.
    * They are roughly the same as your postal code! They don't necessarily point at one unique website, it just points to some computer.
    * They typically look like `185.199.111.153`.
3. The browser goes and contacts the computer residing at that IP address.
4. If the website is properly configured the browser and the server will perform a handshake where they share a bit of information about themselves.
5. During this handshake, for sites whose name ends up starting with `https://` the connection is secured using *Transport Layer Security (TLS)*.
    * TLS involves a whole extra step in the handshake, **it's super important when you're dealing with important stuff**, like your personal information!
    * Only during this handshake the browser show any sort of *actual* identification.
    * If the `https://` isn't in the final address you land on, you should be not trust it to be a legitimate site.
    * In some cases, insecure sites with `http://` do exist and are safe. It's OK to browse them, just verify the information you read, and don't enter any information you don't want to shout to the *entire planet*.
6. Once the handshake is done, your browser and the server have a pipe between them, and they can send each other files of any variety.
7. The server sends whatever the requested file is back to the browser.
    * In the case of `hoverbear.org` there is a default address of `https://hoverbear.org/index.html` that the browser requests.
8. Depending on the *file extension* (the part after the dot in: `page.html`, `image.jpg`, `download.tar.gz` `text.txt`) the browser does the best job it can displaying it.
    * In cases involving an HTML file (the ones ending in `.html`) the browser often ends up requesting more files from the server.

When you visit the very best websites in the world, all of this happens super fast! The **golden standard** is under 100ms from typing in a url (like `hoverbear.org`) to the content displaying on the page. On complex sites like Wikipedia, Zhihu, or Bon Appetit this can take a tremendous amount of effort. On simple sites like the ones we're making, it's very easy!

Here's an example request timeline for the kind of website you'll build, requesting it from a rainy island in the pacific northwest of Canada:

{{ figure(path="firefox-network-debugger.jpg", alt="`hoverbear.org` showing the all important `DOMContentLoaded` event in 75ms. Captured from Firefox Network Debugging Tools.", colocated=true) }}

Simplicity comes with benefits!

## The Power Tools

In order to craft a website you can fall in love with creating, we'll pick up a couple tools that I really admire, I hope you can grow to like them too.

The first thing we need is a web browser, since it's how we visit websites. [Firefox Developer Edition](https://www.mozilla.org/en-CA/firefox/developer/) is really great tool to use for this task! It's just like the normal Firefox you might already be familiar with, but it includes a few extra features that developers (like yourself!) might appreciate. You're also welcome to use the normal version of [Firefox](https://firefox.com) for our purposes.







## The Project

## The Core Concepts

## The Techniques

## The Host

## The Friendly Robot

## The Publish

## The Domain

## The Path Forward