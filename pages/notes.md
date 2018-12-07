---
layout: post
title:  "Notes (discord pins)"
date:   2018-11-23 21:00:00 -0500
categories: jekyll update
---

# Bowser frame hops (or4ng33xp0)

It takes 32 frames for Bowser to jump and fall back to the floor, where he spends another 16 frames before hopping again. After 5 hops, you just need the Timer3 value to not be 0 so that he'll do another "wait 16 frames, then hop".

5 frames for Bowser to fall to the floor after the random Timer3 value is chosen

\+ (16 frames on the ground + 32 frames in the air) * 5

245 (0xF5)

So you either need 0xF5 and above or 0xF6 and above...not sure which side of the "off-by-one" error we're on :P

That's 11 or 12 good values out of 128 (because the random value is set to between 128 and 256), so 8.6% or 9.4%

...

6 hops = 11/128 = 8.6%  
5 hops = 48/128 = 37.5%  
4 hops = 48/128 = 37.5%  
3 hops = 21/128 = 16.4%  

# Powerup grab/damage frame #s (Tompa) [src](https://pastebin.com/sySbjFAd)

Mario -> Super = 47 frames  
Super -> Mario = 47 frames  
Super -> Leaf  = 23 frames  
Leaf  -> Super = 23 frames  
Super -> Fire  = 30 frames  
Fire  -> Super = 23 frames  

# Bowser routine logic (or4ng33xp0)

Mario spawns Bowser like other enemies, due to scrolling within some range. When Bowser spawns, he is
in his "Wait for player" mode, waiting until the screen has scrolled all the way to the middle of the
room and for the player to land on the ground before being set to "Do movements" mode. One of his
timer values (Timer3) is set to 48 on this frame. Timer3 is decremented every frame.

Bowser has 4 internal states while in his "Do movements" mode:

0 - "Fall to floor"  
1 - "Jump and land on floor"  
2 - "Align and fall"  
3 - "Bust floor and look around."  

#### State 3 - Bust Floor and Look Around

He starts off in the "Bust floor and look around" state while falling for the first time. He stays in
this state for the 48 frames that the Timer3 value is set. When Timer3 hits 0, it is set to a
random byte that is grabbed from index 4 of the random array (memory address 0x0786), and Bowser's
state is changed to "Fall to floor". The top bit Timer3 is manually set, so the value will always be forced to
between 128 and 255. In the current Any% NoWW (Warps) TAS, this random value is 248.

#### State 0 - Fall To Floor

In "Fall to floor", Bowser will hop up and down, waiting 16 frames each time he hits the ground to
hop again. He'll also breath fireballs based on another random value that determines how many frames
between each fireball (between 96 and 159).

When Timer3 again hits 0, the game will wait until Bowser has hit the ground (if he was in the
middle of a hop) before setting a "Jump Delay" timer to 176. This timer is decremented every frame,
and when it hits 128 (after 48 frames), Bowser's internal state will be set to 1 ("Jump and land on floor"),
at which point he'll immediately do his big jump.

Knowing this, you can calculate how many frames Bowser will hang around before his first big jump based on which frame you scroll the screen to the middle and cause him to go into "Do movements" mode. But it sounds like you've already speed-hacked to find experimentally when the next frame is that gives you a long enough window before the first big jump to kill him before that happens.

In the TAS, the first fireball is shot when Timer3 is at 13 when Bowser is still in the
"Bust floor and look around" state, and the last fireball (the "kill shot") can be shot 2 frames
after the Timer3 value hit 0 while in the "Fall to floor" state. This makes up a total of about 263
frames required before Bowser's big jump. Depending upon where Bowser is in his hops, it appears the
maximum value that Timer3 would need to be set to in order to still kill him before his first jump
is 202 (hex 0xCA). This was calculated by taking 263 - 13 frames in "Bust floor" state - 48 frames
of "Jump Delay" = 202.

I did some manual memory editing on the TAS, and a value of 198 (0xC6) was still good enough, due
to Bowser being in the air from a little hop when Timer3 hit 0.

# Boss pattern (TheHaxor)

I made a video explaining how boss patterns are determined in general and a couple videos for the common W4 and W5 fire kills in warpless since I've had some people asking me about it recently and there doesn't seem to be a great resource that exists to my knowledge. I pretty much had to learn how to do them from other people's VODs.

Boss pattern introduction: <https://www.twitch.tv/videos/313176738>  
Common World 4 warpless fire kills: <https://www.twitch.tv/videos/313176739>  
Common World 5 warpless fire kills: <https://www.twitch.tv/videos/313176740>  

# Early hammer (or4ng33xp0)

I've been working a bit on cleaning up my Early Hammer pastebin and adding some images and animations. It's definitely not done yet and could use some better images and gifs, but I figured it's probably at least a little more helpful than a wall of text.

[smb3.bf0.org](http://smb3.bf0.org/)

# SMB3 rom assorted patches (narfman0)

[github narfman0/romhacks](https://github.com/narfman0/romhacks)

# Notes on pspeed (Tompa)

Here are some notes on the P-meter: [pastebin](https://pastebin.com/TdUqKgcx)

If your speed is over 40 and you land, while you have P-speed activated, you'll always be able to keep it. Less than 40 speed, then you'll only keep it if you jump on the earliest frame, or have previously hit a wall, and a few other exceptions

# Lemmy fire kill (Horsedad / ilm)

On a unrelated note, ILM showed me this really cool Lemmy firekill today that lets you avoid having to rely on bouncing off his back. It's slightly slower, but far, far more consistent. To be clear, this is all ILM's creation. <https://www.twitch.tv/videos/281359865>

# Hammer bro movement direction item (Tompa) [src](https://pastebin.com/7gZRRiZx)

After a Hammer Brother has moved, it will always face a specific direction. This way you can tell which HB that has which item.
 
HB1: Facing Right  
HB2: Facing Left  
HB3: Facing Right  
 
World 1: HB1 = Star  
World 2: HB1 = Music Box    HB2 = Hammer    HB3 = Flute  
World 3: HB1 = Star         HB2 = Hammer  
World 4: HB1 = P-Wing       HB2 = Star      HB3 = Cloud  
World 5: HB1 = Star         HB2 = Music Box HB3 = P-Wing  
World 6: HB1 = Hammer       HB2 = Cloud     HB3 = Star  

# 6-10 P-Speed Fire Grabs from Big Mario (2 methods) (Kirua) [src](https://www.twitch.tv/videos/105484752)

# Boom Boom hammer glitch (mitchflowerpower)

Glitchy boom boom kill [youtube](https://youtu.be/Z_dhOjulIgs)

# SMB3 bingo (mitchflowerpower)

this should be the most updated ver of bingo with the cards link [Super_Mario_Bros._3_USA_Rev_9.nes](https://cdn.discordapp.com/attachments/121413022731337732/396115380076281859/Super_Mario_Bros._3_USA_Rev_9.nes)

Instructions: https://bingobaker.com/view/1451346

Click the play online to have your card, window capture in OBS or whatever it is that you use

Refresh and or edit link will change the card to setup for a new one.

# All forts route guide (Cujo) [src](https://docs.google.com/document/d/1n16AFOPGwFfTmSnErjU1dRpM2M8KhprRqBztqyvjVek/edit#heading=h.qq45edsb0zox)