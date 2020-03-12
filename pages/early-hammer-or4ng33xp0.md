---
layout: post
title:  "Early Hammer or4ng33xp0"
date:   2020-03-11 18:00:00 -1000
categories: notes eh earlyhammer early hammer
---

# Early Hammer

Early Hammer is the name given to the scenario in World 2 when the Boomerang Brother that holds the hammer moves across the 2-sun level and possibly even 2-3 in order for the player to get a hammer before playing those levels. If the hammer is used on the block below 2-3, up to three levels can be skipped (2-3, 2-sun, and 2-5), saving a speedrunner roughly a minute.

The Boomerang Brothers in  World 2 start out in the following positions:

![World 2 Hammer Brothers' starting position]({{ site.baseurl }}/assets/eh-or4ng33xp0/w2-bros-starting-lg.png)

# No-death Early Hammer

A no-death Early Hammer is the situation where the Hammer moves across 2-3 after the player completes the fort. Due to the rules hammer brothers follow when they move, the only way for this to occur is for both the Hammer and the Music Box to land on top of each other so that they march together to the left across 2-3.

After completing 2-1, the Hammer must move up and the Music Box must move to the right (he can go either up or down at 2-sun, it doesn't matter).

![World 2 Hammer Brothers' Post-2-1 positions]({{ site.baseurl }}/assets/eh-or4ng33xp0/w2-bros-post-2-1-lg.png)

After 2-2, the Hammer must go up again, and the Music Box must end up between the mushroom house and 2-4.

![World 2 Hammer Brothers' Post-2-2 positions]({{ site.baseurl }}/assets/eh-or4ng33xp0/w2-bros-post-2-2-lg.png)

After 2-fort, the Hammer must go left across 2-4, and the Music box must move to the mushroom house and back so that both the Hammer and Music Box end up on the same tile. At this point, they have the chance to walk together down to 2-sun, left twice to 2-3, and then split so that both end up accessible to the player without playing 2-3.

![World 2 Hammer Brothers' Post-2-Fort positions]({{ site.baseurl }}/assets/eh-or4ng33xp0/w2-bros-post-2-f-lg.png)

# Hammer Brother Movement Mechanics and Rules

Hammer Brothers and other overworld map objects (the HELP sprite, the World 7 nippers, the spade card game, etc) are tracked in an array of up to 15 different objects. Each object is referenced by its index into the array. The World 2 Boomerang Brothers are index 2 and 3.

| ![Overworld Map Object Arrray]({{ site.baseurl }}/assets/eh-or4ng33xp0/object-array.png) |
|:--:|
| *Super Mario Bros. 3's object array for World 2* |

Hammer Brother movement is determined by the random number array on multiple frames. Mario 3's random numbers are stored in a 9-byte array. The 72-bits of the 9-byte array are shifted right through the array, with input bits being determined by an XOR-feedback of bit 6 and 14. On each frame, the bits are shifted right once.

| ![Random Number Array]({{ site.baseurl }}/assets/eh-or4ng33xp0/rng.gif) |
|:--:|
| *The array of random numbers are shifted on each frame.* |


There are a couple exceptions to the array being shifted on _every_ frame (most notably, lag frames), but that is outside the scope of this document. Although the random number array contains 9 bytes, the very first one is never used, most likely due to its functionality as the "seed" byte. When needing a single random number check, the game typically looks at the second byte in the array.

After a level ends, the game transitions through a number of states to clean things up and get ready for the player to move around on the overworld map. During the first of these states, an initial direction is chosen for the Hammer Brother to face. To decide which direction the Hammer Brother faces, the byte corresponding to the Hammer Brother's object index is chosen from the random number array. The random number array is indexed off of the second byte so that the first byte is not used. The two least-significant bits from the random byte chosen for the given hammer brother are used to determine the direction it is facing. 0 = Right, 1 = Left, 2 = Down, and 3 = Up.

| ![Choosing which way the hammer brothers should face]({{ site.baseurl }}/assets/eh-or4ng33xp0/face.gif) |
|:--:|
| *The Hammer Brothers' facing direction is chosen before the level card is flipped.* |

However, the hammer brother sprites can only face left or right, since there is no up- or down-facing sprite. If the Hammer Brother is facing Right (0), the right-facing sprite will be used. In all other cases, the left-facing sprite will be used. So although the hammer brother may look like it is facing left, its true direction may be left, down, or up. This is important because a hammer brother will choose to march in the opposite direction of the way it is facing only if it has tried to move in all the other directions first.

In the animation above, the array of random numbers contains `[0xC2 0x3B 0xBF 0xC8 0xB7 0x26 0x48 0x04 0x94]` on the frame the facing direction is determined. The music box (index 2) will choose byte `0xC8` (two bytes from the 2nd byte in the random array). The two least-significant bits of `0xC8` are `0b00`, so the music box bro will face right, and the right-facing sprite will be used. The hammer (index 3) will choose the byte `0xB7`, whose two least-significant bits are `0b11` (decimal 3). Therefore, the hammer will face up, and the left-facing sprite will be used.

Some number of frames later (variable depending upon what needs to be done during the intermediate states), the first movement for the Hammer Brother marching is decided. The logic to do this is somewhat complicated, but it boils down to a fairly simple set of rules. The random number array is again accessed in the same way it was for the initial direction determination. The two least-significant bits are used again to decide direction to march. The most-significant bit of the random byte is used to determine if the value will be incremented or decremented while trying directions. If it is a 1, the value will be incremented. If it is a 0, it will be decremented.

| ![Choosing which way the hammer brothers should move]({{ site.baseurl }}/assets/eh-or4ng33xp0/move.gif) |
|:--:|
| *The Hammer Brothers' movement direction is chosen a number of frames after the facing direction is determined.* |

For example, in the animation above, the array of random numbers contains `[0x16 0x8E 0xA3 0xBE 0xF9 0x84 0x77 0x7F 0x91]`, the music box bro (index 2) will choose byte `0xBE` (two bytes from the 2nd byte in the random array). The most-significant bit of `0xBE` is `0b1`, so the direction value will be incremented while checking the directions until a valid direction is found. The two least-significant bits of `0xBE` are `0b10` (decimal 2). The first direction tried will be the value incremented by 1. 2 + 1 is 3 (Up). The game then checks the direction chosen to see if the Hammer Brother is allowed to walk that way. If it can't march up, it will then choose right (0). A hammer brother will not try the direction opposite of the one it is facing unless that is its only option. In our example, the music box bro originally faced right, so it will not move left until that is its last option. However, its second choice of 0 (Right) is a valid movement, so it will move right.