---
layout: post
title:  "CQRS productivity"
date:   2019-11-24 13:11
categories: productivity design
image: https://upload.wikimedia.org/wikipedia/commons/a/a5/Barack_Obama_and_his_entourage_walk_through_the_Kremlin.jpg
excerpt: <p>...it's like travelling with an entourage of super skilled personal assistants.</p>
---
# Productivity principles to live by & how I apply them

When I'm trying to focus on the task at hand I want to deal with disruptive thoughts or actions without losing my current train of thought or working context.

For example, I can be writing an article, remember that I need to send an urgent message but then get sucked into reading unread messages as I open my inbox en route to actually composing that new message. Many minutes later I'm still in my inbox or on a completely different track of activity after reading an unrelated message(s) - that original article is long forgotten and the time allocated to getting it done is wasted.

### I just need the UI where I can type & send my message - why am I forced to confront my cluttered inbox in the process?

Changing visual contexts even for a few seconds can destroy my concentration on a task. That's especially disruptive as a programmer where it often takes a long time to re-engage and rebuild the mental house of cards you need to create fresh solutions and/or decipher thorny abstract problems.
However, I often find that engaging my conscious brain in deep thought has the unexpected side effect of my unconscious brain remembering or coming up with all sorts of good ideas and TODOs. Those mental popups are usually worth capturing to revisit later and sometimes warrant rapid action.*


*\* Of course sometimes other people or external forces are the source of interruption too.*

### So what's the best way to juggle these intrusive sparks of inpiration?

> The dream scenario is that you can delegate, dispatch or schedule any task nomatter what you're doing or where you are with the absolute minimum required tooling or context.

I like to imagine that it's like travelling with an entourage of super skilled personal assistants on hand at any time. They're either ready to run an errand on my behalf, or they've magically got the kit I need to complete various tasks in the heat of a moment, or they dilligently capture my commands for execution later when it's more convenient. Most busy VIPs, executives and leaders are afforded this privilege...but what about the rest of us plebs?

It's hard to beat a notepad and pen in the pocket as a cheap & cheerful minimum viable solution for capturing ideas and todos on the fly for deferred triage and action. Pen & paper will always be a solid fallback option for that reason, but we need digital tools to match the digital realm if we want to realise our solo productivity potential.

Whereas you can easily open a notepad to a fresh page to jot down thoughts without reading through every previous entry, software is notoriously contrary. Instead typical UI design results in bundling and burying the tools you need to issue key commands behind the output of unrelated distracting content or notifications.
Computer science includes a concept called Command Query Responsibility Segregation (CQRS) that addresses the essence of my frustration with that habit: retrieving information and modifying data are 2 different wokflows that deserve to be handled differently.

Luckily I've found a few fantastic examples of software designed with a clear appreciation for this principle, and they're helping me inch closer to that ideal digital-entourage of executive assistants.
##Here's a small selection of highlights:

### 1. [Todoist](www.todoist.com)

	Adding a fresh task is beautifully efficient - you're presented with the minimal interface required, at the touch of a keyboard shortcut or mobile widget.

	[![Image from Gyazo](https://i.gyazo.com/14c159e8fc016038fc9f906afd6185c0.gif)](https://gyazo.com/14c159e8fc016038fc9f906afd6185c0)

### 2. [Alfred](https://www.alfredapp.com/)

	Universally available search & action dispatching tool for MacOS (similar to native Spotlight but with much more extensibility). It's so powerful that it probably deserves its own article / presentation. One recent example that I set up is adding the currently playing track on Spotify to a playlist without having to focus the Spotify window.

	[![Image from Gyazo](https://i.gyazo.com/ecf4beaadf4948117a686b477f4db312.gif)](https://gyazo.com/ecf4beaadf4948117a686b477f4db312)

### 3. Android widgets

	Android app widgets often enable a direct link to the action that you want. Here's an example of the "add TODO" widget from Todoist in action, very similar to the desktop experience. You'll notice I have a few other direct action widgets setup on my homescreen like compose new email, check the weather, create new calendar event, speed dial Wifey, and "Shazam that track"!


  <video style="height:100%;" controls>
    <source src="https://lh3.googleusercontent.com/YbWGcEc0Kp3i4N9sLBIrHXSZ1VDa3Qp8f7yXvbh0X7l-w1I1djD9rAn1a_eBR7udWxAwjwbvuOvEd0cAmlrXD_k38snlNhuV1cXNFn0YOVH5h77Sw2jaoiDxWMRXIs96wq05DaGjq-c=m18" type="video/mp4">
  </video>

### 4. [Bookmarklets](https://www.thetechbasket.com/most-useful-bookmarklets/)

	Bookmarklets can be used like app widgets to take you straight to the screen or action of an existing webapp. Some of my favourites include shortcuts for creating new Google Drive documents in a single click, without having to load all my folders first. Also, I use [this link](https://mail.google.com/mail/u/0/?ui=2&view=cm&fs=1&tf=1&shva=1) for navigating directly to Gmail's compose new email view (and as a bonus I have it set to a keyword search shortcut of "c" for rapid execution).

### 5. [Red hot timer](https://apps.apple.com/us/app/red-hot-timer/id929960914)

	Time-boxing tasks with the Pomodoro technique is a really effective habit for me. Red Hot Timer is a native MacOS app that enables setting a new timer rapidly from a keyboard shortcut or a quick click & drag of the mouse from the menu bar. No messing about, just "set it, and forget it" functionality with a very clean UI for configuring multiple countdown timers with a variety of options.

	[![Image from Gyazo](https://i.gyazo.com/fd0e79a97012d3c4855ad9260562e4bb.gif)](https://gyazo.com/fd0e79a97012d3c4855ad9260562e4bb)

There's much more room for elegant solutions within this problem-solving domain and I'm always keen to hear recommendations and nurture relevant efforts. Share your favourites in the comments below 🤓.
