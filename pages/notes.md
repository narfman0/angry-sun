---
layout: post
title:  "Notes"
date:   2018-11-23 21:00:00 -0500
categories: notes
---

# [5-6 exit pipe crushing (Lui)](#5-6-exit-pipe-crushing-lui)

If you touch the side of the screen at max walking speed or more, it's possible
to clip ahead by 2 pixels and get crushed. Tap right without running from a full
stop before hitting the right side, then hold right into it without risking
a death.

# [6-10 P-Speed Fire Grabs from Big Mario (2 methods) (Kirua)](#6-10-p-speed-fire-grabs-from-big-mario-2-methods-kirua-src) [src](https://www.twitch.tv/videos/105484752)

# [6F3 clip (Mizumaririn)](#6f3-clip-mizumaririn-src) [src](https://docs.google.com/spreadsheets/d/e/2PACX-1vS4Axtw1CdX6a-ZcQ-9c35ezIcMfAyCo2RXcQu8z_iRI25ZU6-TkEw4bscTZQvG-m4dRHiiVlXMRc8O/pubhtml#)

# [7-1 duck clip data](#7-1-duck-clip-data) [src](https://docs.google.com/spreadsheets/d/1_Hyan9UidoyHolYwe1nmx4CPzMQ-rPLozf83IeRvor8)

# [7-1 subpixel manipulation](#7-1-subpixel-manipulation)

[Lui video](https://youtu.be/69ykM4gXbsA)
[MFP video](https://www.youtube.com/watch?v=e8IJpquq69c)

After you kill Lemmy (world 6 airship), there is some time before the wand grab. Position yourself under the
wand and come to a stop. Tap right as briefly as possible. If Mario does not move right a pixel, keep
pressing single frame inputs to the right. If Mario moves a pixel, stop and wait for wand. When Mario
doesn't move, the subpixel is incrementing higher. We want a low subpixel value though, so when he does
move the single pixel, this means the subpixel is very low with only whatever remainder is left after
incrementing Mario's x position.

# [7-7 practice rom info (Lui)](#7-7-practice-rom-info-lui-src-rom-patch-link) [src](https://pastebin.com/kkpta9JH) [rom patch link]({{ site.baseurl }}/assets/patches/smb3practice_7-7.ips)

HUD features: ![Lui description]({{ site.baseurl }}/assets/notes/7-7epic.png)
 
The following are some of the most commonly encountered values for the X/Y coordinates while attempting to clip
 
|X1 | Y1    | X2   |   Y2       |   description                          |
|---|-------|------|------------|----------------------------------------|
|AF | F/0/1 | B3   |   2/3/4    |   bad lineup (-1.5 px)                 |
|B0 | F/0/1 | B3   |   2/3/4    |   bad lineup (-1 px)                   |
|B0 | F/0/1 | B4   |   2/3/4    |   bad lineup (-0.5 px)                 |
|B1 | F/0/1 | B4   |   2/3/4    |   clip                                 |
|B1 | F/0/1 | B5   |   0/1      |   bad lineup (+0.5 px)                 |
|B2 | F/0/1 | B5   |   0/1      |   bad lineup (+1 px)                   |
|B2 | F/0/1 | B6   |   0/1      |   bad lineup (+1.5 px)                 |
|   |       |      |            |                                        |
|AD | D/E   | B1   |   F/0/1    |  clip, positions logged a frame early  |
|B1 | E     | B4   |   1        |  good lineup, but jumped a frame late  |
 
Lineup is essentially luck based, so the goal is to be within 3.5 pixels off of the good X coordinates, since Mario's max running speed is 3.5px/f.
 
Note that the ranges of Y positions that may work can vary:
- with a low jump (low 3x Y speed), F/0/1 on frame 1 then 2/3/4 on frame 2 should be good
- with a higher jump (high 3x up to 45 Y speed), E/F/0 on frame 1 then 2/3/4 on frame 2 should be good
Low jumps are recommended of course, but avoid having under 30 Y speed near the pipe.
 
Also, landing on the pipe gives a position of 0, or 1 for a frame, and that's usually logged on the 2nd frame.

# [7-7 zip strategy guide (Lui)](#7-7-zip-strategy-guide-lui-src) [src]({{ site.baseurl }}{% link pages/7-7-zip-strategy-guide.md %})

# [8-2 fire sun patterns (czikubi)](#8-2-fire-sun-patterns-czikubi)

[youtu.be/Cz4sdr3VsZQ](https://youtu.be/Cz4sdr3VsZQ)

# [Airship Rewards](#airship-rewards)

* World 1 - P-wing
* World 2 - Cloud
* World 3 - Music Box
* World 4 - P-wing
* World 5 - Cloud
* World 6 - P-Wing
* World 7 - N/A

# [Boom Boom hammer glitch (mitchflowerpower)](#boom-boom-hammer-glitch-mitchflowerpower)

Glitchy boom boom kill [youtube](https://youtu.be/Z_dhOjulIgs)

# [Boom Boom firekill, hops, and overkill (or4ng33xp0)](#boom-boom-firekill-hops-and-overkill-or4ng33xp0)

It's crazy how the developers decided to program boom booms. They gave them 37
hitpoints and looked at when they hit 32 hitpoints to have
the boom boom change states and turn into the orb. The boom boom is actually never
"killed." Most objects have a "killed" state, and the boom booms never use that
state...they're always in the "normal" state.

When two fireballs hit on the same frame, it takes the boom boom to 31 hitpoints, so the
game never sees the 32 hitpoints. You then have to either stomp on him 3 times or hit him
31 more times to cause the upside down orb overkill.

# [Bowser frame hops (or4ng33xp0)](#bowser-frame-hops-or4ng33xp0)

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

# [Bowser routine logic (or4ng33xp0)](#bowser-routine-logic-or4ng33xp0)

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

# [Early hammer (or4ng33xp0)](#early-hammer-or4ng33xp0-src) [src]({{ site.baseurl }}{% link pages/early-hammer.md %})

# [Firekill morton (assemble_me)](#firekill-morton-assemble_me)

Assemble wrote a spreadsheet to further detail morton behavior: [src](https://docs.google.com/spreadsheets/d/e/2PACX-1vTgyb-gTH6rrxQI4_5KIJqMx6vrXKZRhKid6vg9a5XLYuf4e3VeI0qnpUuAI3jKjOc9ySScmPryQ6lf/pubhtml)

# [Firekill patterns [warpless] (teex)](#firekill-patterns-warpless-teex)

I (teex) made a playlist of pretty much all the boss patterns you'll typically encounter in Warpless. 

Each clip is comprised of:
- the firekill
- the pattern by itself (simply watching the boss's opening moves for recognition purposes
- screenshots & footage of any manipulations or conditional setups wherever applicable

[youtube playlist](https://www.youtube.com/playlist?list=PLjSZGQNren-IWJHjf6HQev-PE7bdYW4LE)

[doc](https://docs.google.com/spreadsheets/d/1sTi9g2cxaNCVkCTQ-Ez4mKshAD7zTKG3uK1pb1ys6oc/edit#gid=0)

# [Firekill patterns (TheHaxor)](#firekill-patterns-thehaxor)

I made a video explaining how boss patterns are determined in general and a
couple videos for the common W4 and W5 fire kills in warpless since I've had
some people asking me about it recently and there doesn't seem to be a great
resource that exists to my knowledge. I pretty much had to learn how to do
them from other people's VODs.

Boss pattern introduction: <https://www.twitch.tv/videos/313176738>  
Common World 4 warpless fire kills: <https://www.twitch.tv/videos/313176739>  
Common World 5 warpless fire kills: <https://www.twitch.tv/videos/313176740>  


# [Firekill savestates (yatokami9)](#firekill-savestates-yatokami9)

Intended for everdrive n8 pro!

#0: standard W1
#1:  Hundo W2
#2: mov 1.5 W2
#3: Wendy
#4: W4 mov2
#5: W5 mov1
#6: Ignore, its an impossible W5 pattern
#7: hundo W5
#8: W2 OSWG practice
#9: W6 subpixel manip practice
#10: W5 OSWG practice
#11: W6 Fire kill
#12: Hundo W7
#13: Warpless W7 (boxing with one inventory movement after fort)
#14: Duck clip practice 7-1
#15: Hundo W4

[Download zip]({{ site.baseurl }}/assets/notes/firekill_savestates.zip)

# [Firekill savestates (thebagler5)](#firekill-savestates-thebagler5)

Intended for nestopia!

[Download zip]({{ site.baseurl }}/assets/notes/firekills.zip)

Create two practice roms named `smb3_firekill_practice` and `smb3_firekill_practice2`,
and extract the savestates in the nestopia save dir.

`smb3_firekill_practice` 1 = Larry post 1-6 bro fight, 2 = Morton movement of 1, 3 = Wendy,
4 = Iggy movement of 0, 5 = Morton movement of 2, 6 = Roy shoot first pattern,
7 = Roy movement of 1 pattern, 9 = Iggy movement of 2
`smb3_firekill_practice2` 1 = Larry pre 1-6 bro fight, 2 = Lemmy, 5 = Iggy movement of 1

# [Fort acceleration difference (tompa)](#fort-acceleration-difference-tompa)

After collecting an orb, you'll be frozen the first frame when
entering a stage. This means the acceleration frame rule will be different, as
it starts ticking on level load, compared to not getting an orb.

If you hold right when entering a stage, you'll accelerate up to speed 6 then
the acceleration frame rule ticks in and you'll not increase to speed 7 the
following frame but will instead stay at 6.

If a fort was beaten, you'll get up to speed 5 before being stopped for a frame.
That freeze frame also makes it impossible to jump in midair in 4-4 if you beat
the fort previously, and it will also decrease the number of frames you can
jump at the start of a castle from 2 to 1.

Max non-pspeed speed is 40, and there are 16 subpixels. 40 goes into 16
twice with a remainder of 8. Thus, speed will oscillate between two because the
remainder (8) is half of the total values. This means the subpixel values
will oscillate with different values after orb collection levels vs after
regular levels.

# [Frames by action](#frames-by-action)

| Frames | Action |
| 32 | One HB movement |
| 17 | One map movement |
| 16 | Buffered map movement |
| 31 | Flower power up animation |

# [Frog%](#frog_src) [src]({{ site.baseurl }}{% link pages/frog-percent.md %})

# [Game Genie Codes](#game-genie-codes)

KKKZSPIU YPXXLVGE AEUGNSSL

As far as I know these are the 3 best Game Genie codes to use if you want to practice on console. I don't know exactly which code is which, but it gives you access to a world select and life counter on the opening screen, (Up/Down to change world on the left, A to add on 5 more lives) gives you a full inventory with the ability to reuse items, as well as letting you re-enter normal stages. Forts, airships, and odd levels like the pyramid are unable to be re-enter after completion, so you'll have to suicide in the level or reset to get back into them.

| Code     | Effect                 |
| OOKXGLIE | PUPRLE SWIMMING RACOON |
| OXKZELSX | Super speed running    |
| EAYIXX   | Mario will die in one hit, regardless of what form he’s in. Do not add ending spaces. |
| SLXPLOVS | Infinite lives         |
| AASZAZYP | Everyone Throws Fireballs [Except Hammer Mario] |
| ZPKUVAKX | Multi Colored Levels, neat color pallet change |
| OEOZGEGT | Turns Flying Koopas Into Hammer Bros. When Stomped |

# [Hammer bro bonus items](#hammer-bro-bonus-items-src) [src](https://themushroomkingdom.net/codes/smb3)

![Hammer bro bonus items]({{ site.baseurl }}/assets/notes/hammerBroBonus.png)

# [Hammer bro movement direction item (Tompa)](#hammer-bro-movement-direction-item-tompa-src) [src](https://pastebin.com/7gZRRiZx)

After a Hammer Brother has moved, it will always face a specific direction.
This way you can tell which HB that has which item.

| World | Item      | Facing | # |
|-------|-----------|--------|---|
| 1     | Star      | R      | 1 |
| 2     | Music Box | R      | 1 |
| 2     | Hammer    | L      | 2 |
| 2     | Flute     | R      | 3 |
| 3     | Star      | L      |   |
| 3     | Hammer    | R      |   |
| 4     | P-Wing    | R      | 1 |
| 4     | Star      | L      | 2 |
| 4     | Cloud     | R      | 3 |
| 5     | Star      | R      | 1 |
| 5     | Music Box | L      | 2 |
| 5     | P-Wing    | R      | 3 |
| 6     | Hammer    | R      | 1 |
| 6     | Cloud     | L      | 2 |
| 6     | Star      | R      | 3 |

# [Hitboxes](#hitboxes-src) [src]({{ site.baseurl }}{% link pages/hitboxes.md %})

# [Lemmy fire kill (Horsedad / ilm)](#lemmy-fire-kill-horsedad--ilm)

On a unrelated note, ILM showed me this really cool Lemmy firekill today that
lets you avoid having to rely on bouncing off his back. It's slightly slower,
but far, far more consistent. To be clear, this is all ILM's creation.
<https://www.twitch.tv/videos/281359865>

# [Level Durations](#level-durations) [gdrive SMB3 Times](https://docs.google.com/spreadsheets/d/18W3TCmSC8W1Pc7zgWVCE__EgjsElkyOsgMIycCj0ifs/edit)

# [maps](#maps) [nesmaps](https://www.nesmaps.com/maps/SuperMarioBrothers3/SuperMarioBrothers3.html)

# [N-Spade card game](#n-spade-card-game)

There are 8 solutions to the nspade card game, shown below.

![nspade-card-game-solutions]({{ site.baseurl }}/assets/notes/cardSolutions.png)

A runner can invest some time identifying the solution then getting two fire flowers.
The first fire flower can be used after 5-1. This allows for fire kill in 5-F1.
This second fire flower can be used after wall-jumping 6-9. This allows for 6f3 zip,
faster 6f3 door entry, boom boom firekill, and 7-2 fast pspeed.

See [felo's card strat]({{ site.baseurl }}{% link pages/warpless-51pwing-felo.md %}) for details and route.

# [N-spade warpless route](#n-spade-warpless-route)

For warpless, we are allowed to spawn the n-spade card game over levels in order to play
the n-spade game and mark the level completed. In order to do this, we need to spawn
the game over a level, and there is a level in which this saves time in warpless: 3-6.
Some of the theory is covered in [mitchs youtube video, here](https://www.youtube.com/watch?v=0WbrKENJZxc&pp=ygUYbWl0Y2hmbG93ZXJwb3dlciBuLXNwYWRl) and cujos pastbin, copied and linked on this site.

In order to get the card to spawn on 3-6 for warpless, we must do the following:

1. Fight a hammer brother to the left of 2-4 (either bro is fine, ideally hammer and skip box)
2. After HB left of 2-4, play the pyramid
3. After pyramid, play the airship
4. After airship, use hammer to destroy the block in world 3
5. After destroying the block, play the roulette game
6. After the roulette game, you will hear the nspade card spawn. Note, it coincides with the HB left of 2-4's x and y position on the map.
7. Play everything normally up to 3-6.
8. Ideally, we skip the star in all of world 3
9. Play the n-spade game. This is a good opportunity to pick up a fire flower or two, potentially for after 5-1 and after 6-9.
10. Play 3-7 (only if you skipped the star bro) and get cloud. This means we have two extra clouds: one unused from 3-6, and one we just collected
11. Play 4f1 :D we used the hammer in early world 3
12. Consider using pwing in 5-1 and equipping fire flower after 5-1
13. Consider walljumping 6-9 and equipping fire flower after
14. Consider clouding 7-9, 7f2, and 8f with your two extra clouds

Note: 3-7 collecting cloud is ~31s, 8F is ~41s, 7f2 is ~32s depending on your
route. 4-4 is another candidate cloud level if you have hammer for 7f2 (they
are very close timewise)

Note2: if you have to fight the w3 star, we need to line up with bridge, so
skip 3-7. It's a nasty timeloss but unavoidable :shrug:


# [Offscreen wand grab offset script (lui)](#offscreen-wand-grab-offset-script-lui)

[gh.com offsetsplits.py](https://github.com/narfman0/smb3-tools/blob/main/offsetsplits.py)

# [Powerup grab/damage frame #s (Tompa)](#powerup-grabdamage-frame-s-tompa-src) [src](https://pastebin.com/sySbjFAd)

Mario -> Super = 47 frames  
Super -> Mario = 47 frames  
Super -> Leaf  = 23 frames  
Leaf  -> Super = 23 frames  
Super -> Fire  = 30 frames  
Fire  -> Super = 23 frames  

# [Pspeed notes (Tompa)](#pspeed-notes-tompa-src) [src](https://pastebin.com/RFss7BXN) 

Note: old notes here, I think completely redundant [src](https://pastebin.com/TdUqKgcx)

Useful memory addresses:
03DD: P-meter
0515: Counter for next P-meter.
056E: How long P-speed will last in midair
 
Once Mario speed reaches 40, the P-meter will start increasing. Will show up as the following numbers in the RAM watch:
1 -> 3 -> 7 -> 15 -> 31 -> 63 -> 127.
 
The P-meter runs on a timer, it will go up every 8 frames. Once the timer hits 0, Mario must have 40 speed, be on land and hold B for the P-meter to increase.  While the timer is counting down, Mario may be in midair or have his speed less than 40.
 
If Mario doesn't fulfill the critera when the counter reaches 0, he'll drop one P-arrow and a 24 frame counter will start, unless you only got one arrow, in which case it will just be 0 on the timer and P-meter. When the timer hits 0, it will continue as before, to check Mario's speed etc.
 
During these two timers, you can slow down your speed and quickly regain it before the timer hits 0. With the first timer, the one that counts to 8, you have a limited time to do so. The optimal way for a TAS, for shortest distance, is the following:
 
Speed: 40, 38, 36, 35, 36, 37, 38, 39, 40
Timer: 00, 07, 06, 05, 04, 03, 02, 01, 00
 
This is done with the following inputs:
Nothing (40), left (38), left (36), nothing (35), right (36), right (37), right (38), right (39), right (40).
 
However, this method is not always possible. Because of the acceleration framerule, or whatever you want to call it... Every 8th frame, you can't increase your speed. And for the same frame, you won't lose speed if you use no directional button (As done at "nothing (35)". If the frame rule would occur for speed 36-40, this method would not work, as I wouldn't be able to hit speed 40 in time. Which means I can't decrease as much speed as seen in the example.
 
For a real time run, the best would likely be to release Right quickly and then repress it. Though hitting the timing right would be tricky. As releasing the button too early would mean you might release it at the time the counter hits 0, meaning you'll decrease your P-meter. And releasing too late means you can't get back the speed before the timer hits 0. It's hard to have some sort of visual cue for this, as the P-meter will visibly be increased 2 frames after the timer hits 0.
 
In order to get a use of this, you practically need to do it several times/P-meter arrow. Could possibly be done if you get the timing right. Go nuts, I guess!
 
Another thing to note. When you have a full P-meter, and make a jump. A 256 timer will start (Going from 127 -> 0, counting down every second frame). If Mario hasn't landed on ground, such as if you would jump on several enemies in a row, the P-meter will drop to 0, but you will still keep your P-speed of 56 speed. Once you land, your speed will start decreasing to 40, during this time a new P-meter will start. Though if you would land on the frame rule where your speed can't be decreased, as mention above, you can keep your speed of 56. This is used in the TAS to keep the sliding speed for example.
 
If you land when the 256 timer is going, it will reset to 0. With the exception of if you jump the first frame you land. It will then continue to count down.
 
With Racoon/Tanooki Mario, the 256 timer works differently. Here it is not reset if you land on ground, but will continue counting down until it hits 0. If you are in midair when this happens, you won't keep your speed as you would without the a tail. The speed you'll end up with depends on a couple of factors. The speed frame rule, if you jumped and for how long and if your speed is above or below 40.

# [Max speeds (Tompa)](#max-speeds-tompa-src) [src](https://pastebin.com/cVFCvpbf)

The various top speeds you can have in SMB3. The number is how many subpixels you move/frame. 16 subpixels make up a whole pixel.

| Max Speed | Condition |
| 8  | Being pushed by the wall in an autoscroller. |
| 11 | Walking uphill. |
| 16 | Scrolling through walls/slow swim with Frog. |
| 20 | Running uphill. |
| 22 | Attached by Micro Goomba. |
| 23 | Flying. When you start flying, you may have more speed, but the speed will eventually drop down to 23. |
| 24 | Walking/swimming. |
| 27 | Walking downhill |
| 32 | Fast swim with Frog. |
| 40 | Running. |
| 41 | Jumping with Frog Suit, you can accelerate from 39 to 41 speed units/frame with the frog. |
| 43 | Running downhill |
| 48 | Speed of Mario's fireballs |
| 56 | P-Speed |
| 57 | P-speed with Frog Suit, you can accelerate from 55 to 57 speed units/frame with the frog. |
| 59 | P-speed downhill. |
| 63 | Sliding downhill. |
| 64 | Boosted by spinner. |

# [Reset to clear ram (e.g. wrong warp) (kabaudio)](#reset-to-clear-ram-eg-wrong-warp-kabaudio)

Do you have to hard reset/power off for several seconds to get wrong warp? What normally temporal values stick around in reset?

If playing on original console, certain crashes can actually fill the stack (Ram $0100 -> $01FF) with garbage values. 
Because this particular part of ram is NEVER cleared by the game's reset logic (only the stack pointer is initialised to FF), nor any ram clear routines (they always leave the stack), it means that if you get a crash that does change the stack ram, you can end up being spat out of the glitched pipe the wrong direction, because it actually reads part of the stack as tile data for the glitch pipe as Mario travels down it.

Certain values tell the pipe logic to change direction like left, right, up down etc (only on vertical pipe maze levels which have bendy pipes)

So if your unlucky, you might be on a PB paced run, go down the pipe, and be spat back out the top. 

Since resetting on console doesn't help clear the stack, the easiest way to do so is to power off for a few seconds, then power back on, as this allows the Ram values to decay from lack of power, and thankfully the power on state appears to be in a way that doesn't affect the pipe glitch (but no one knows what it actually starts on - as its uninitialised)

This is never a problem on emulator, as emulators generally fill all ram at power on / reset with
| $0000 | 0 0 0 0 F F F F 0 0 0 0 F F F F |
| $0010 | 0 0 0 0 F F F F 0 0 0 0 F F F F |
| etc | etc |

You only really need to do a hard power off and on sequence after a crash. 

Examples on console:

[Zikubi doing all forts wrong warp, clip here](https://clips.twitch.tv/NaiveSmilingPelicanCoolStoryBob):

His old console actually had a very finicky ram chip that would even hold bad values after power off and on. We found an ice pack to lower the temperature of the ram chip helped (power on ram states can be affected by temperature)

Also [happened to Kirua, clip here](https://www.twitch.tv/kirua/clip/ExquisiteTenuousKathyTriHard)

I assume you'll be attempting the shell throw setup next so prepare for plenty of crashes :wink:
If you need any other info feel free to DM me.

# [Route Comparison (Lui)](#route-comparison-lui-src) [src](https://docs.google.com/spreadsheets/d/e/2PACX-1vTzbqZb96uT2mP5Y11l9E_YZdCYWh_hChzw_v05kGzbjUeVm1_ZPpEl2lq0oYa7eikTvw3gqkAZSUS5/pubhtml#)

# [Simulated w2 RNG (lui)](#simulated-w2-rng-lui-src) [src](https://discord.com/channels/747566475753029643/824185359284830219/1172586399019569192)

| post 2-3 eh | 1.8%|
| 1 death eh | 0.51%|
| 0 death eh | 0.05%|

# [Simulated w3 RNG (lui)](#simulated-w3-rng-lui-src)  [src](https://discord.com/channels/747566475753029643/824185359284830219/1175089402305843260)

simulated w3 rng 1 million times up to before clouding 3-6 and this is what i got:

| description | matches | rate |
|no runaway | 727457 | 72.75% |
|runaway with at least 1 death required | 247399 | 24.74% |
|hammer runaway and star is skippable | 1014 | 0.10% |
|runaway and both bros are skippable | 15274 | 1.53% |
|runaway and both bros are skippable but optional comeback is possible (subset of the above) | 9322 | 0.93% |
|runaway with unskippable star unless hammer is fought | 8499 | 0.85% |
|runaway with unskippable star and hammer right of 3-6 | 211 | 0.02% |
|runaway with unskippable star and hammer right of 3-8 | 146 | 0.01% |

# [Simulated w6 RNG (lui)](#simulated-w6-rng-lui-src) [src](https://discord.com/channels/747566475753029643/824185359284830219/1175107655283511318)

got 61.4% chance of skipping star bro in w6 also

# [SMB3 RTA Wiki](#smb3-rta-wiki)

[smb3rta.wikia.com](http://smb3rta.wikia.com/wiki/SMB3RTA_Wiki)
 
Slightly outdated, but still has some decent information. I might look into getting this more up-to-date as the days go on.

# [Votes](#votes)

See [votes]({{ site.baseurl }}{% link pages/votes.md %}) for details.

# [Zip/clip windows (mfp)](#zipclip-windows-mfp)

Looking for feedback: the window for 7-1 standing appears much smaller than 7-6 standing?

| Level | Frames | Notes |
| 6-9 | 0-5 | small mario, 2 frame window |
| 7-1 | 14-15 | standing clip |
| 7-1 | 0-6 | duck clip |
| 7-6 | 3-10 | standing clip |
