---
layout: post
title:  "Early Hammer"
date:   2018-11-14 17:44:50 -0700
categories: jekyll update
---

(Copied from Tompa's Pastebin at http://pastebin.com/qrqFaxj2)

Early Hammer Probability

The movement of a Hammer Brother is purely depending on the RNG address(es). Mainly if the number is even or uneven. When you complete a level, you'll notice that the HB is either facing to the left or to the right. Left for uneven numbers and right for even. When it is time to move, after the level card has been flipped or, in the case of a death, Mario is moved back to where he came from, the HB will make their move and once again check what value the RNG has at the moment.

Facing right: Moving up or to the right. Impossible to move to the left

Facing left: CA

Standing above 2-3: Facing right will mean the HB is forced to go down. For the turn, the RNG value will once again be checked. If even: Moving down, if uneven: Moving right. Standing above 2-3: Facing left will mean the HB can go either Left or Down. Down with an even RNG number and left for uneven.

Result:

Even = Down (50% chance)
Uneven + Even = Down (25%)
Uneven + Uneven = Left (25%)

75% chance of moving down, 25% chance to the left.

The leftmost HB's starting position is between 2-3 and 2-Quicksand. If he moves, he'll have four spots to end up on. But what will the fact say?!

EVEN RNG: He'll face right. Facing right means a HB can't move to the left if he is able to move to the right. So right it is in this case. Then he'll turn up if the RNG is even at the turn and own if uneven.

UNEVEN RNG: He'll face left. When facing left he can movie either to the left or the right.

 
Even-Even:      Right
    Even:       Up      Above 2-Quicksand:
    Uneven:     Down    Below 2-Quicksand:
   
Even-Uneven:    Right
    Even:       Up      Above 2-Quicksand:
    Uneven:     Down    Below 2-Quicksand:
 
Uneven-Uneven:  Right
    Even:       Up      Above 2-Quicksand:
    Uneven:     Down    Below 2-Quicksand:
   
Uneven-Even:    Left
    Even:       Up      Above 2-3
    Uneven:     Down    Below 2-3

So for the four spots it might end up with, here is the chance for it:

Above 2-Quicksand:  3/8
Below 2-Quicksand:  3/8
Above 2-3:          1/8
Below 2-3:          1/8x
 
Even-Even-Even
Even-Even-Uneven
Even-Uneven-Even
Even-Uneven-Uneven
Uneven-Even-Even
Uneven-Even-Uneven
Uneven-Uneven-Even
Uneven-Uneven-Uneven

The first movement for the second HB can be either up, downdown or downleft:

 
Even-Even: Up
 
Even-Uneven:    Down
    Uneven:     Left   
    Even:       Down
   
Uneven-Uneven:  Up
 
Uneven-Even:    Up
 
Up: 75%
Downleft: 12.5%
Downdown: 12.5%

Let's compare with the fastest Early Hammer pattern you can get, which the TAS is using: HB1 needs to go above 2-Quicksand and HB2 moves up. That gives us these RNG patterns to work with:

Even-Even-Even
Uneven-Uneven-Uneven

Being 2/8 or 25% chance of getting the right pattern for the first move.

For the second move. HB1 needs to go left into the mushroom house and HB2 up again.

 
HB1:
Even-Even-Even=DownDown
 
U-U-U: Right (Will bump into HB2 and move back left)
 
 
HB2:
U-U-U: Up (Will bump into HB1 and move back down)
E-E-E: Up

Early Hammer No Deaths is not possible if HB2 moves down. So Even-Uneven-Even and Even-Uneven-Uneven won't work, 25% chance of failing.


If the HB is facing to the right, it is impossible for it to move left.

Even number -> Facing right -> Even when moving -> Moving up

The number for which they are facing takes in effect as soon as the level starts fading in when completed/if you die.


http://pastebin.com/GCmS60PB

The Random Number Geneator is located on address 0781, 1byte, in the emulator. It's an address that "randomly" jumps between different numbers each frame. These values are between 0-255 for a total of 256 values. The generator sets in effect as soon as you start the game and will continue to count for every frame. It will never reset and it can't be altered in any way.

As everything, it it technically not random. It will always go through the same series of numbers. For example, the first 10 numbers when you power on the game will always be: 136, 68, 34, 145, 72, 36, 18, 137, 68, 34

There is actually a pattern with the values. The next value is the half of the previous one. Though 34/2 doesn't equal 145. Though: 145+145=290 290-256=34. I currently don't know why it sometimes do that however.


Hand levels: Even value = grabbed. Uneven = Pass 
