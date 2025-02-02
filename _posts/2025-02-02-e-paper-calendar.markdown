---
layout: post
title:  "E-paper Calendar"
date:   2025-02-02 12:39
categories: e-paper diy
excerpt: <p>Build summary for e-paper digital calendar</p>
---

![e-paper-calendar photo2](../public/images/ecal2.jpeg)

I always wanted a calendar on the wall that would auto update with details from my Google calendar so that I could look at my phone less without the risk of missing important commitments. E-ink seemed like a great choice but seemed prohibitively expensive when I first looked into buying a small screen way back in 2015.

Fast forward to 2022 and I was fortunate enough to be gifted a [Waveshare 10.3inch e-paper display](https://www.waveshare.com/wiki/10.3inch_e-Paper_HAT) from our [company CTO](https://jgc.org) who was pursuing [similar e-paper-driven tinkering](https://blog.jgc.org/2023/03/barebones-project-showing-how-to-get.html)...just weeks before I was due on parental leave for the first time - amazing timing!

However, it wasn't until I was on parental leave for the second time last year that I actually found the sweet spot overlap of time, energy and motivation to finish version one of my e-paper calendar.

Of course it took even longer to actually write up the build steps; this time prompted by a close friend who's just embarked on their own fatherhood journey and is keen to make their own version.

In short, I found a great tutorial elsewhere that quickly got me to a point where the e-paper display was connected to the pi and I could iterate through design ideas for what to display. I kept tweaking the python with the help of some AI copilot prompting to arrive at our kitchen dashboard.

So far, on top of calendar events for the week, it fetches tasks from a Todoist, the weather forecast, and a random wisdom quote each day.


## Ingredients
- raspberry pi zero 2 + [a 40 pin connector](https://mauser.pt/catalog/product_info.php?cPath=1874_640_2570_792&products_id=012-0073)

  ![40-pin connector](
    https://ampyrxbtyq.cloudimg.io/v7/_mauserimages_/product_image/2018/309/5bbc1e20c5d2ad5b5f8bda4e4a4fabf6_012-0073.jpg?trim=3&func=fit&margin=2p&bg_colour=ffffff&width=150&height=150&force_format=webp&ci_sign=e8bfd130297beab3e4d71943e53ddae183102719
  )

- SD card (minimal space required so any will do)
- [Waveshare 10.3inch e-paper display](https://www.waveshare.com/wiki/10.3inch_e-Paper_HAT)
- empty 860g Weetabix box
- [a detailed tutorial to get up & running](https://www.instructables.com/E-paper-Calendar-Raspberry-Pi-With-E-ink-Screen-an/)
- [some Python flair](https://github.com/jonnyparris/e-paper)

![e-paper-calendar photo1](../public/images/ecal1.jpeg)
![e-paper-calendar photo4](../public/images/ecal4.jpeg)

## Build details

### 1. Connect the Waveshare driver board to the pi zero, via the 40pin connector. - soldering required.

The Pi Zero 2 is great because it's small & inexpensive and yet it comes Wifi-ready. The downside is that you need to do a bit of soldering to connect pins to the board, although it took way less time to solder the 40 pins than I bargained for. The main complexity is in setting up the board & pins so they're fixed in place while you work, while being easy to reach all of them.

![e-paper-calendar photo3](../public/images/ecal3.jpeg)

### 2. Follow the tutorial!

[here](https://www.instructables.com/E-paper-Calendar-Raspberry-Pi-With-E-ink-Screen-an/)

### 3. Tweak the code

I uploaded my final python file here https://github.com/jonnyparris/e-paper - it's expecting to find a few extra file assets and environment variables in the same folder when it runs (e.g. fonts and api secrets).

### 4. [Cut a hole in the box...](https://www.youtube.com/watch?v=Rt0spqQtMKg&t=2s&pp=ygUNZGljayBpbiBhIGJveA%3D%3D)