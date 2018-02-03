---
layout: post
title:  "Building my first FPV drone from scratch - part 2"
date:   2018-02-03 21:19
categories: fpv diy
excerpt: <p>Build progress on my first FPV quadcopter</p>
---

From [part 1 of this series](2018-01-06-fpv-drone-building-part1.markdown), you may recall **the plan so far**:

0. Buy the parts
1. Assemble the parts <-- I AM HERE
2. Learn to fly FPV
3. Fail, fix, improve
4. Strap lasers to the whole setup!

### Putting things together
I am *still* waiting for my FPV goggles to arrive from Banggood. My original order in December was clearly lost somewhere along the journey but customer support have resent one without any fuss. However the new one is still in transit from Belgium 2 weeks later.

On the other hand, the re-sent battery arrived in just a couple days. With that, I felt confident to start the epic road of assembling the quadcopter knowing that I had a means to test whether my connections were functional.

I have been diligently following the steps outlined in the $99 quadcopter build tutorial from UAVFutures. However, there have been a number of key details that were either glossed over or just not mentioned in that original video so I've had to update the recipe slightly. I'm jotting down my *actual* build steps here to help both myself and anyone else that may face similar problems starting the hobby as an absolute beginner.

Despite the surprise extra steps, I really enjoyed discovering many more brilliant FPV dronebuilding content creators and resources across the web. It really seems to be a hobby that has attracted a wealth of passionate and generous personalities.

#### Build Recipe (Pics to be included...)
1. Screw motors onto the base frame
2. Screw ESC board into middle of frame
3. Solder the motors to the ESC
4. Solder battery connector to PDB
5. Solder ESC to PDB
6. Screw PDB on top of ESC
7. Solder VTX & Camera to each other, and to [FC](https://github.com/cleanflight/cleanflight/blob/master/docs/Board%20-%20SPRacingF3.md)
8. Solder FC to PDB
9. Screw FC on top of PDB
10. Solder Rx to FC
11. Make sure Rx is bound to your Tx (radio)
    
    My FlySky i6S (v3.0) came with a quickstart guide that was a little too quick. You might want to check out the [full pdf manual](https://www.flyingtech.co.uk/sites/default/files/product_files/FS-i6S-MANUAL-EN-20161001.pdf) too in order to  understand this bit of kit in a bit more detail.

12. Update FC firmware
    
    This step was particularly painful as I somehow managed to 'brick' (render completely useless & unresponsive) my flight controller. This was additional stress *after* a hunt to find the appropriate drivers to enable my Macbook to recognise that the FC was connected via USB.

    Luckily, you can recover a bricked controller by following a few straightforward steps. However, a key requisite for that involved creating a shortcircuit between 2 holes in the board (labelled 'boot'). After much panic that I might have to solder something horrific and then de-solder it, I realised that a bit of tin foil would do the trick just fine.

    ##### CleanFlight vs BetaFlight - what software should I be using to setup my FC?
    [**BetaFlight**](https://github.com/betaflight/betaflight-configurator/releases/latest) started as an evolution of CleanFlight in order to test new features. It quickly became a better performing all-round stable product but the name had already stuck. So BetaFlight ftw.

    ##### How to get BetaFlight to recognise your FC plugged in via USB on Mac
    i. Try this [VCP driver download](http://www.ftdichip.com/Drivers/VCP.htm).
    
    ii. Try [this one too from Silicon Labs](https://www.silabs.com/products/development-tools/software/usb-to-uart-bridge-vcp-drivers) in case the first one didn't make a difference.

    ##### How to recover a bricked SP Racing F3 FC by flashing the proper firmware.

    i. Short circuit the boot sockets on your FC
    
    ii. Choose your firmware to flash with the following options enabled
        
        - "No reboot sequence"
        - "Flash on connect"
        - "Full chip erase"
        - "Manual baud rate" set at 256000
    iii. Power on the board - Betaflight should flash (aka install) the firmware as soon as it connects. You'll know when it's done when the red light on the FC starts flashing (and it'll say so at the bottom of the BetaFlight window).
    iv. Power off the board and remove the boot shortcircuit.
    v. The board should work as expected when you reconnect the power

13. Setup Tx to output on correct channels
14. Verify FC receives on correct channels
15. Match FC config to motors wiring setup
16. Remove throttle spring on Tx

    Painless 360 has an excellent video walkthrough on this that also helped explain the mystery strip of metal that was also included in the box of my FlySky FS i6S (v3.0).
    <iframe width="560" height="315" src="https://www.youtube.com/embed/-7d1e8L2jb4" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

17. Verify power and control of motors <- I AM HERE
18. Activate all the heatshrink (now you're sure that you won't need to resolder any joins)
18. Attach propellers
19. Maiden voyage
20. Setup goggles to receive camera footage via VTx
21. Maiden FPV voyage

### Some helpful resources for both now & later
- [Cheap tips to make FPV flying easier](https://irjayjay.blogspot.co.uk/2017/05/cheap-ways-to-improve-your-fpv-flying.html)
