---
layout: post
title:  "TAS Notes"
date:   2023-12-03 13:11:00 -0500
categories: resources tas notes
---

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
| 5 | Walking uphill underwater, steep slope. |
| 6 | Walking uphill underwater, normal slope. |
| 8  | Being pushed by the wall in an autoscroller. Walking underwater. |
| 10 | Walking uphill, steep slope. Walking downhill underwater, normal slope. |
| 11 | Walking uphill, normal slope. Walking downhill underwater, steep slope. |
| 16 | Scrolling through walls. Slow swim with Frog. |
| 19 | Running uphill, steep slope. |
| 20 | Running uphill, normal slope. |
| 22 | Attached by Micro Goomba. |
| 23 | Flying. When you start flying, you may have more speed, but the speed will eventually drop down to 23. |
| 24 | Walking/swimming. |
| 26 | Walking downhill, normal slope. |
| 27 | Walking downhill, steep slope. |
| 32 | Fast swim with Frog. |
| 40 | Running, no P-speed. |
| 41 | Jumping with Frog Suit, you can accelerate from 39 to 41 speed units/frame with the frog. |
| 42 | Running downhill, normal slope. |
| 43 | Running downhill, steep slope. |
| 48 | Speed of Mario's fireballs |
| 56 | P-Speed |
| 57 | P-speed with Frog Suit, you can accelerate from 55 to 57 speed units/frame with the frog. |
| 58 | P-speed downhill, normal slope. |
| 59 | P-speed downhill, steep slope. |
| 64 | Sliding downhill. Boosted by spinner. |
