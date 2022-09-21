---
layout: post
title:  "Practice ROMs"
date:   2018-11-14 17:44:50 -0700
categories: practice roms
---

## ROMs

There are three (current) variants of our current practice ROM. Provided are

1. rom link - direct links to the rom or information about it
2. patch link - the IPS (binary) patch file based against the (common) PRG0 SMB3 .nes file.
Running [RomPatcher.js](https://www.marcrobledo.com/RomPatcher.js/) or [Lunar IPS](https://www.fusoya.eludevisibility.org/lips/)
to patch the PRG0 rom should yield the target practice rom.

### Current

- Lui has extended fcoughlin and dotsarecool's work. Included in the zip are
patches for regular practice, pspeed with dots, and a subpixel practice rom
patch for 7-1/7-6/7-7/7-9
  - [patch link]({{ site.baseurl }}/assets/patches/smb3practice_20220313.zip)

- Lui has created a firekill practice rom. Usage:
1. Go to the desired world
2. powerup before entering a level the distance from the castle you wish
3. press select to increment the leftmost number in score (which represents
how many movements the bro will take when exiting the level)
4. press select-start to exit the level
5. go to the airship as normal
You will get the pattern you selected with the 'select' button.
  - [patch link]({{ site.baseurl }}/assets/patches/smb3movements.ips)

### Historical patches

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

### [SMB3 Race Edition](#smb3-race-edition)

MaCobra made a race edition, which is also a candidate for a future tournament rom.
It is speedrunners edition minus autoscroller edits, or, nohands + HB movements of one.

Download [v1.7 PRG0 version here]({{ site.baseurl }}/assets/patches/smb3_race_edition_v1.7_PRG0.ips)

### [Romhacking SMB3](http://www.romhacking.net/games/750/)

### [Route Randomizer](https://sites.google.com/site/smb3randomizer/home)

### [SMB3 bingo (mitchflowerpower)](#bingo)

this should be the most updated ver of bingo with the cards link [Super_Mario_Bros._3_USA_Rev_9.nes](https://cdn.discordapp.com/attachments/121413022731337732/396115380076281859/Super_Mario_Bros._3_USA_Rev_9.nes)

Instructions: https://bingobaker.com/view/1451346

Click the play online to have your card, window capture in OBS or whatever it is that you use

Refresh and or edit link will change the card to setup for a new one.

## Notes

Some generic patches recommended for all of the above

- noauto -removes autoscroller from the game
  - [patch link](https://github.com/narfman0/romhacks/blob/master/Super%20Mario%20Bros%203%20noauto.ips?raw=true)

- nodeaths -removes decrement of lives upon enemy death. it removes some code paths that slow down gameplay and never worry about restarting worlds
  - [patch link](https://github.com/narfman0/romhacks/blob/master/Super%20Mario%20Bros%203%20nodeath.ips?raw=true)

- nocards -removes all random card encounters, normally triggered every time a players score passes a multiple of 80000.
  - [patch link](https://github.com/narfman0/romhacks/blob/master/Super%20Mario%20Bros%203%20nocards.ips?raw=true)

- MaCobra misc patches [github macobra/smb3-hacks](https://github.com/macobra52/smb3-hacks)

- narfman0 misc patches [github narfman0/romhacks](https://github.com/narfman0/romhacks)
