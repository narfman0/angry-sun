---
layout: post
title:  "Practice ROMs"
date:   2018-11-14 17:44:50 -0700
categories: practice roms
---

## ROMs

There are three (current) variants of our current practice ROM. Provided are 1. rom link - direct links to the rom or information about it
and 2. patch link - the IPS (binary) patch file based against the (common) PRG0 SMB3 .nes file. Running Lunar IPS to patch the PRG0 rom
should yield the target practice rom.

- fcoughlin created the standard version, which hard-codes debug mode (start screen lives and stage select, select button cycles powerups, full infinite world map items) and includes hammer brother delete and stage reentry.
  - [rom link](https://www.dropbox.com/s/yqgl5k0qi9si5en/Super%20Mario%203%20Practice%20ROM.nes?dl=0)
  - [patch link]({{ site.baseurl }}/assets/patches/Super Mario 3 Practice ROM.ips)

- dotsarecool augmented fcoughlin's ROM and created a version that allows start-select stage exit and adds dots on the screen at P-speed check points.
  - [rom link](http://www.dotsarecool.com/twitch/smb3pspeed.html)
  - [patch link]({{ site.baseurl }}/assets/patches/smb3pspeed.ips)

- Lui's builds off dots' further. Description: not much new, but i’ve replaced the anchor with something that looks like a poison shroom that makes you small mario on the map, also added some meme easter egg which may or may not be useful, see if you can figure it out
  - [rom link](https://cdn.discordapp.com/attachments/121413022731337732/502671645924655124/smb3practice.nes)
  - [patch link]({{ site.baseurl }}/assets/patches/smb3practice.ips)

- Lui's 7-7 practice rom
  - [rom link](https://cdn.discordapp.com/attachments/121413022731337732/565682523091501056/smb3practice_7-7.nes)
  - [patch link]({{ site.baseurl }}/assets/patches/smb3practice_7-7.ips)

- Lui's 7-1 wrong warp practice rom
  - [patch link]({{ site.baseurl }}/assets/patches/smb3ww_dotsless.ips)
  smb3ww_dotsless.ips

- Zikubi's 7-1 wrong warp practice rom
  - [patch link]({{ site.baseurl }}/assets/patches/smb3practice_7-1.ips)
  smb3practice_7-1.ips

## Alternatives

### [SMB3 bingo (mitchflowerpower)](#bingo)

this should be the most updated ver of bingo with the cards link [Super_Mario_Bros._3_USA_Rev_9.nes](https://cdn.discordapp.com/attachments/121413022731337732/396115380076281859/Super_Mario_Bros._3_USA_Rev_9.nes)

Instructions: https://bingobaker.com/view/1451346

Click the play online to have your card, window capture in OBS or whatever it is that you use

Refresh and or edit link will change the card to setup for a new one.

### [Romhacking SMB3](http://www.romhacking.net/games/750/)

### [Route Randomizer](https://sites.google.com/site/smb3randomizer/home)

## Notes

Some generic patches recommended for all of the above

- noauto -removes autoscroller from the game
  - [patch link](https://github.com/narfman0/romhacks/blob/master/Super%20Mario%20Bros%203%20noauto.ips?raw=true)

- nodeaths -removes decrement of lives upon enemy death. it removes some code paths that slow down gameplay and never worry about restarting worlds
  - [patch link](https://github.com/narfman0/romhacks/blob/master/Super%20Mario%20Bros%203%20nodeath.ips?raw=true)

- nocards -removes all random card encounters, normally triggered every time a players score passes a multiple of 80000.
  - [patch link](https://github.com/narfman0/romhacks/blob/master/Super%20Mario%20Bros%203%20nocards.ips?raw=true)

- others here: [github narfman0/romhacks](https://github.com/narfman0/romhacks)
