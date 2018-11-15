---
layout: post
title:  "Hardware Guide"
date:   2018-11-14 17:44:50 -0700
categories: jekyll update
---

Short answer: Serious runners will want a NES. Serious streamers will want an RGBNES.

Gameplay quality
----------------

### Emulators

The cheapest and easiest way to get into SMB3 running is an emulator running on a PC, as virtually any consumer hardware available is capable of running a ROM of the game. (Disclaimer: Be sure you have a legal copy of the game.)

-   Advantages
    -   Cheapest option available.
    -   Savestates are effortless and unlimited.

-   Disadvantages
    -   *Significant* input lag.
    -   Varying degrees of inaccuracy.

### Official/Unofficial Nintendo Hardware Emulation (WiiVC, NESClassic, RetroUSB AVS)

These platforms are on par with accurate emulators and generally considered acceptable for runs.

-   Advantages
    -   Savestates are available.

-   Disadvantages
    -   Costs money.
    -   Some lag on WiiVC version on modern displays.

### SNES (Super Mario All-Stars/Collection)

Game is very close to original but has significant time-wasting features. A fuller description is [here](http://earlyhammer.net/index.php/Version_Differences#NES_vs._All-Stars "Version Differences").

-   Advantages
    -   Much-loved SNES controller
    -   Responsiveness and physics same as original

-   Disadvantages
    -   Time-wasting animations and other features
    -   Awkward/expensive play and capture with modern hardware

### NES

Original game, gold standard for runners.

-   Advantages
    -   Original brick controller considered best for game
    -   Tight and responsive d-pad
    -   NTSC-U is the fastest version of game

-   Disadvantages
    -   Awkward/expensive play and capture with modern hardware

Video Quality
-------------

Some videophiles and streamers want to know how to get the highest-quality picture from their setups. Here is video quality, ranked from best to worst:

-   HDMI (NES Classic, AVS), inside-computer emulators
-   RGB video (RGBNES, SNES (preferably with RGB amp mod), PAL Wii)
-   Component video (RGBNES w/ component add-on, SNES w/ Retrovision cables, NTSC Wii)
-   S-Video (Modded NES, SNES, Wii)
-   Composite (NES, SNES, Wii)
-   RF (NES, SNES)

### 240P

NES and SNES users need to be aware that plugging their consoles into their modern flatscreen TVs is not likely to yield good results. These older consoles, in order to save computational power, used a video format called 240p that used every other scanline on the TV. While this worked fine with CRTs, flat panel screens were not designed to interpret this format correctly. Sometimes they are able to use the signal, but almost always this results in significant input lag.

#### Best solution: Split to CRT

There are "video splitters" (sometimes called distribution amplifiers) available that are designed to take one video source, duplicate it, amplify it to original strength, and send it to more than one destination. This can be used to supply a capture card, such as the GV-USB2, with a signal at the same time as the CRT television, which will result in whatever lag your capture card applies being rendered irrelevant.

Less commonly, some TVs also have "pass-through" outputs that will take your input video signal and output it to another destination such as a capture card. This negates the need for a distribution amplifier.

#### Second-best solution: XRGB Framemeister

The XRGB Framemeister, by Micomsoft Japan, is designed with the retro-gamer in mind. It takes multiple kinds of video signals from retro consoles and converts them to formats modern flat panels understand, with very low lag (often 3 frames). On the downside, it is very expensive, usually $350 or more, to acquire one.

Flash Carts
-----------

Those who use real hardware often want to take advantage of the savestates that emulator players enjoy. There are several kinds of flash carts available that will allow you to quickly save and load states efficiently.

#### Everdrive N8

This is a newer, more popular flash cart, made by Krikzz in Ukraine. This cart only allows one active savestate per game, but is more compatible with a wide variety of games.

#### RetroUSB Powerpak

This is an older-model flash cart, made by RetroUSB in California. It has lower compatibility with other games but has five savestate slots for practice.

#### Super Everdrive / SD2SNES

If you are practicing the Super Mario All-Stars version, bear in mind that the Super Everdrive and SD2SNES do not have native savestate capabilities. You will need an external device, such as a Nakitek Gamesaver, to practice on such a device.

#### A Note on Chinese Knockoffs

On eBay, you may encounter suspiciously low-priced flash carts. These are very likely Chinese copies of original flash cart hardware, very similar to the originals but likely varying in compatibility with some titles, likely incompatible with firmware upgrades, and absolutely not supported by the manufacturers. As SMB3 was an incredibly popular game, these carts are likely to run this game faithfully but the buyer should beware.

#### A Note on Flash Cart RTA Attempts

There is a problem unique to Nintendo's NES hardware that makes classification of flash cart runs as original hardware problematic. Nintendo shipped their consoles with an extremely limited amount of addressable RAM, requiring game manufacturers to use a feature called "mappers" inside their carts in order to expand the RAM (and other features) the hardware could use in-game. The issue with this is that these mappers need to be emulated inside the flash cart in order for the majority of NES titles to function.

There are strange bugs that can occur uniquely on flash carts. They are extremely rare, but do happen, and at least 1-2 have been documented on SMB3 in particular. As a result, there is an ongoing debate on whether or not flash cart attempts should be classified as "emulator" attempts. Those using NES hardware should avoid this by simply using a real cart for attempts. These are common and relatively cheap; around $15 USD on eBay as of this writing.
