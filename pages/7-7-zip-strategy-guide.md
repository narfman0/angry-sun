---
layout: post
title:  "7-7 Zip Strategy Guide (Lui)"
date:   2021-07-25 21:00:00 -0500
categories: lui 7-7 strategy zip guide
---

# 7-7 Zip Strategy Guide (Lui) [src](https://docs.google.com/document/d/1OUvuJz851edNEYWJbdROtf4TWp3UEsJgoS0QeNE2WAc/edit#heading=h.b6rm87sp2bez)

## Introduction

The 7-7 zip is an advanced strategy, so it will be assumed that you, the reader, are already somewhat familiar with Mario’s physics and the basic mechanics behind clipping.
This guide will show a particular setup for the zip that, while being precise, relies entirely on the player’s execution, as well as provide info on some of the alternative strategies that could also be used with varying degrees of success.
Using the newest version of the 7-7 practice hack is strongly recommended. It can be downloaded here. Its features will be referenced throughout the guide.

## Routing

For this setup, 7-F2 needs to be played right before 7-7. Thus, after 7-8, the level order will be 7-9, 7-F2 then 7-7. There are two reasons behind this routing choice:
the goal orb at the end of the fortress facilitates subpixel manipulation;
clearing a fortress, as opposed to other level types, grants a different alignment for the acceleration framerule. While not essential, the setups described in this guide were tested under this condition.
The strategies used in the levels preceding 7-F2 will not affect the setup.
Note that, compared to playing 7-7 before 7-9, this route requires 6 extra movements on the world map, sacrificing about 1.8 seconds. Results may vary depending on the player’s execution.

## Subpixel Manipulation

The goal is to clear 7-F2 with a horizontal subpixel value of 0, 1, or 2, in order to carry it over to 7-7. Other subpixel values may not necessarily mean guaranteed failure, as will be seen later, but for the specific setup shown in this guide, the aforementioned window happens to be the most convenient one to aim for.
Outside of how the goal orb is collected, the way the fortress is played doesn’t really matter. However, note that the strategy described in this guide will not work as small Mario, although it’s possible that, in the case of taking damage, a backup strategy could be used instead.

Mario’s current horizontal subpixel value can be found on the HUD, in hexadecimal (base 16):

### How to Subpixel

First, Mario needs to stand on a certain coordinate relative to where Boom Boom (the fortress boss) was defeated, such that once the orb has spawned, it will not be collected until Mario moves just one pixel towards it. The following pictures show the required positioning:
facing left:

facing right:


Note that, in all 4 pictures, Mario is standing on the same exact coordinate relative to where the orb spawns. As implied, either facing direction will work.

Next, Mario needs to move exactly one pixel to the right to collect the orb. This must be done using repeated 1 frame long presses on the D-Pad, to avoid building too much speed and overshooting the desired subpixel window of 0-2. This is very similar to the strategy used for the 7-1 subpixel manipulation, explained here and here.
Note that a 2 frame press will result in either a 2, 4, 5 or 6 subpixel increment (usually 4), and as such, it should be avoided as much as possible in this context.

If the procedure was followed correctly, the fortress will be beaten with a final subpixel value of 0, 1 or 2, ready to be carried over onto the next level.

## 7-7

The zip strategy will be broken down into 3 parts: running to the right and turning back left to build p-speed, jumping towards the left wall and turning back right, jumping into the top corner of the pipe.

### First turn-back

Hold right and B from the start of the level, do a short jump from close to the pipe, then turn left just as Mario touches the pipe itself. This is the most lenient step, with a 3 frame window to press left. The following pictures show what each frame in the window looks like:

There are a couple things to note:
The starting position and height of the jump towards the pipe do not need to be precise.
When switching from holding right to holding left on the D-Pad, having neutral frames (i.e. neither left or right is being held) between the two states does not matter. In fact, right can be released at any time as soon as Mario has jumped off the ground, without any loss of speed.

### Second turn-back

This step involves running to the left to gain p-speed, aiming to start a high jump from a specific spot, then performing a fairly precise turn-back to the right. The jump can be performed sooner or later, based on the player’s preference, and its position will affect the timing of the following turn-back.

The following pictures show several contiguous coordinates that the jump could be started on:


All coordinates are expressed in hexadecimal.
After having performed a jump to the left, its starting X coordinate will be recorded on the HUD:


Depending on where Mario started the jump, the turn-back to the right should be delayed by a certain amount of frames. To give a concrete example, if the jump starting X position was $21, holding left for 16 more frames after the start of the jump until switching to holding right will result in a successful setup, both with or without a neutral frame in between; holding left for 17 frames before switching to right will also work, but in this case there cannot be a neutral frame in between.
Jumping a frame later, meaning from X position $1E, the situation will be very similar, except the turn-backs should be done a frame earlier compared to jumping from X position $21. Specifically, a 15 frame delay before holding right will work with or without neutral frames, while a 16 frame delay will work with no neutral frames only.
Conversely, jumping a frame earlier, meaning from X position $24, the same turn-backs will work if done a frame later compared to jumping from X position $21, and so on.

To recap, the following chart lists the amounts of frames to keep holding left between the jump input and the start of the turn-back, relative to the corresponding jump starting position:

X Position
0 or 1 neutral frames
0 neutral frames only
$26~$27
18
19
$24~$25
17
18
$21~$22
16
17
$1E~$1F
15
16
$1B~$1C
14
15
$18~$19
13
14
$14~$15
12
13
$11~$12
11
12


The amount of frames spent before starting the turn-back and the amount of neutral frames are recorded on the HUD, outlined in red and blue, respectively:


It’s suggested to experiment with frame advance to find suitable cues for the turn-back, or alternatively memorize a rhythm to time it after the jump. For example, the underwater theme from this game has a tempo of ~112.5 BPM, meaning each beat lasts 32 frames, therefore each eighth note ticks every 16 frames.

### Jump into the Corner

This step is not unique to this setup, in fact it should be done the same way regardless, but it will be broken down for completeness.

The most consistent way to get the corner clip is to start a jump from X position $51 and hold the A button for 9 frames. Note that, while it’s possible to zip with gradually higher jumps from further left, or shorter ones from further right, the pacing of Mario’s vertical speed happens to be less favorable in both cases.

For reference, the following pictures show Mario at X positions $4F and $51, respectively:


The starting X coordinate of the jump as well as the duration of the A press in frames are recorded on the HUD, outlined in red and blue, respectively:


It’s recommended to start holding down on the D-Pad just as Mario gets very close to the corner of the pipe. This will ensure that the zip is initiated as quickly as possible, with the added bonus of being unable to accidentally jump out of a successful attempt, even if A is pressed. Letting go of right will not compromise a zip attempt if done after accelerating up to the maximum horizontal speed of 56 subpixels per frame.

## Other Strategies

Aside from the one presented, there are actually many more combinations of inputs and starting subpixels that will result in a successful setup for the zip. Some of them are documented here.
For reference, the instances of working setups previously shown can be found on the 17-21 tab, under the 4, 5 and 6 column sections, columns 18, 18n and 19, and subpixel rows 0, 1 and 2.

Included are also some combinations that work after beating any level other than a fortress, under the “all - standard” tab. While there doesn’t seem to be a convenient range of subpixels with as good of a window as the post fortress setup, it’s still possible to pinpoint a few strategies that should work with nearly half of the possible starting subpixels. The following is an example of such a strategy.

### Post 7-8 Example

The first turn-back is done almost the same way, however the window to start holding left is a frame earlier compared to the post fortress setup. The following pictures show what each frame in the window looks like:


The following chart lists the amounts of frames to keep holding left between the jump input and the start of the turn-back, relative to the corresponding jump starting position:

X Position
0 or 1 neutral frames
0 neutral frames only
$26~$27
19, 20
21
$24~$25
18, 17
20
$21~$22
17, 16
19
$1E~$1F
16, 15
18
$1B~$1C
15, 14
17
$18~$19
14, 13
16
$14~$15
13, 12
15
$11~$12
12, 11
14


Note that in this case, each individual set of inputs has its own working window of either 6 or 8 subpixels out of 16. For more details, consult the “all - standard” tab in this sheet.

The advantage of using this kind of strategy, compared to playing 7-F2 before 7-7, is that it’s possible to follow the optimal level order. This makes it suitable for categories where not all levels need to be played, meaning that backtracking to 7-7 is simply not an option. The trade-off is that subpixel manipulation becomes much less practical, especially as long as there aren’t convenient sets of similar strategies that work with the same easily obtainable subpixels. This is something that could change with future research, but for now the post fortress strategy allows reaching significantly higher consistency.

## LUA Script

Locating some of the possible 7-7 strategies has been possible by analyzing the sequence of inputs done in certain successful RTA attempts. Those inputs were then replicated in FCEUX using a LUA script. Using a script allows automating the process of testing sets of variations on the timing of the inputs of the two turn-backs, essentially brute forcing through thousands of strategies to determine whether each single one of them results in a successful zip or not.

The LUA script in question can be downloaded here. It may be used by running it sometime before the player takes control of Mario inside 7-7. Using fast-forward is highly recommended.
