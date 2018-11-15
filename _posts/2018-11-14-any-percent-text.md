---
layout: post
title:  "Any% Route Text"
date:   2018-11-14 17:44:50 -0700
categories: jekyll update
---



(Copied from Producks' doc at <https://www.dropbox.com/s/ag16d0dthqfkxf0/Mario%203.rtf?dl=0>)

World 1 is pretty much self-explanatory. Since nothing in the first world affect 7-1, I won't touch world 1 at all.

How the glitch works
--------------------

The glitch itself is actually really simple. It consist of using the X enemy position to setup 3 values. Those enemies are positioned in a way where the CPU read the values has a valid assembly instruction.

`JSR $8FE1 = Jump to the end routine`

The values we need to achieve this assembly instruction are the following:

`0x93: 32 0x94: 227 0x95: 143`

If you don't understand any of this, don't worry!

All you need to know is that we need to place 3 koopas on those values to achieve the wrong warp. Simple as that!

The Setup
---------

Before we start with the explanation.

Here a FCEUX movie file that does the setup: <http://bombch.us/CLz2>

Or a youtube video: <https://www.youtube.com/watch?v=n0hrQt90Tys&>

This should work with **PRG0** and **PRG1** since the version has no effect on the glitch. Make sure you're using the **North American version** of the game or the glitch won't work.

First of all, try to enter the door facing left like in the picture. This will make things easier when trying the next jump.

![Producks 1.png](/assets/any_percent/Producks_1.png)

Since we're facing left already, we need to do that really difficult jump. This jump is really easy to mess up and it shouldn't be overlooked when practicing. Here a picture of my visual cue when to jump:

![Producks 2.png](/assets/any_percent/Producks_2.png)
![Producks 3.png](/assets/any_percent/Producks_3.png)

Jump when Mario gets past the 3 pixel line.

Keep watching the video until Mario enter the pipe with the koopa. One thing to note, you might bump your head into this block and that will kill your p-speed.

![Producks 4.png](/assets/any_percent/Producks_4.png)

There's no way to avoid it and it will be one of those things you'll have to deal with.

Once you get out of the pipe, your goal is to kill the piranha plants has fast as you can and skip using the pipes. This is one of those parts where if you go too fast, you'll screw up and one of the plant will be alive. Make sure you kill all of them before flying over! If you follow how I do it in the video it shouldn't be difficult to learn.

Here's a trick that save 1 second that you might not do since it's insanely difficult to pull of consistently.

![Producks 5.png](/assets/any_percent/Producks_5.png)

**This is the first value we are going to setup for the assembly instruction.**

`0x94: 227`

The way you grab the koopa is up to you. This 1 second time save might not be worth it for the risk it bring, but if you're going for the ultimate time, it's a must. Once you have the shell in your hand, all you need to do is hug that block with the shell until you can't move anymore. Then release B to kill it and it should be on the value **227**every time!

![Producks 6.png](/assets/any_percent/Producks_6.png)

**The next koopa to setup is the hardest one by far. There no true way to practice this one since throwing the shell work with your speed and your position. This trick save 3 seconds which is massive for any%. What we're doing is entering the pipe when the shell hit the X value 32.Going down the pipe will despawn it on the correct value if you're lucky which is**\
`0x93: 32`

The last value is sadly really difficult. What we need to do is bring the shell with us when going down the pipe. What we want is grab the shell has fast has as fast as possible and get the pipe clip first try. Even if you get the pipe glitch first try, you'll also need to get lucky. Depending on when you enter the pipe might decide if you can do this setup or not. This is one of those thing we can't control, sometime the glitch room won't display sprite and despawn the koopa in your hand. It will look like this:

![Producks 7.png](/assets/any_percent/Producks_7.png)

As you can see, Mario and the koopa are nowhere to be seen. That mean that your run is dead.

If you don't get that room and you see Mario sprite. You're in business! The last part is a bit tricky. Pay attention to the movie file or video. Before throwing the shell I move right then go back left. This is really important since throwing shell depend on Mario position. If you don't throw the shell on the correct position you will never get the glitch. You'll always get 144 instead of 143.This is what you're aiming for:

![Producks 8.png](/assets/any_percent/Producks_8.png)
`0x95: 143`

The picture show when to press A and the koopa being on the X position 143. This trick isn't that bad when you get the hang of it, but this trick is going to require a lot of practice to get comfortable with it.

Conclusion
----------

If everything went fine, you should warp to the credits. This is the fastest way to achieve this glitch in a RTA speed run. A time of 3:03 should be the ultimate limit with this setup. I don't believe there will be any other way to make things faster unless something major is found. Good luck with the runs and if you have any question feel free to ask them!

Producks
