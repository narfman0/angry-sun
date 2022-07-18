---
layout: post
title:  "Early Hammer Console"
date:   2021-11-05 18:00:00 -800
categories: notes eh earlyhammer early hammer console manip manipulation
---

# Early Hammer Console Manipulation

There lie many challenges in reliably performing early hammer on console. A common strategy currently is to
press a TAS emulator reset hotkey and the NES reset button at the same time, and hope to spot a "wave" in
obs if not synced properly. This document will iteratively seek to make this more reliable.

## Capture card - opencv tool

I've been working on a new tool to read directly from the capture card and match
its output against template images. From there, we can measure latency and sync up
that way. The project lives here: https://github.com/narfman0/smb3-eh-manip

## First latch modifications

The first step is syncing poweron of NES and TAS.

Commonly, speedrunners use [RetroSpy](https://github.com/retrospy/RetroSpy). From the description:

> RetroSpy is designed to present controller inputs from a console or computer in a display window. This allows you to show your controller inputs for things like speedrunning, game tutorials, and more.

RetroSpy works by splicing controller cables such that the cable sends unmodified data to nes. A
a microcomputer can read and interpret the signals, and present them in a custom window. Adapting
modifications provided by [10ooki](https://discord.com/channels/599131748143464459/599134097721524224/905233663380299817), ([see src changes here](https://github.com/narfman0/RetroSpy/commit/73b73e6675a3fa985a4be31871730e3cce51a180),)
we can reliably trigger an action on the host operating system.

The changes make it such that the first latch signal seen by the microcomputer will tell retrospy
every button is pressed. This is important, because we want retrospy to be able to recognize when
a "special event" has happened, so that we can make retrospy automatically emit a keystroke, as if
we pressed a button on the keyboard. We want some unique or impossible signal to lead to a button press.
For example, if retrospy looks for left+right to simultaneously be pressed, we know that cannot happen
on an unmodified controller, so that would be "safe" to emit a button to control a TAS.

### Steps

#### Apply the firmware modifications to the arduino

1. Acquire patched firmware
  * Download prepatched first latch firmware changes [here](https://github.com/narfman0/RetroSpy/releases/download/first-latch-v1/firmware.zip)
  * Observe and apply src code changes [here](https://github.com/narfman0/RetroSpy/commit/73b73e6675a3fa985a4be31871730e3cce51a180)
2. [Install Arduino studuio](https://www.arduino.cc/en/Main/Software_)
3. Ensure the arduino is plugged in via usb
4. Open arduino studio, and File/Open... the `firmware.ino` file in your patched firmware
5. Click Sketch/Verify&Compile
6. Click Sketch/Upload

#### Update keybindings.xml

This updates keybindings to work with the NES and press the "home" button on the keyboard
when the NES is powered on.

1. Open your RetroSpy install directory
2. Update "keybindings.xml" in your RetroSpy directory
  * [Download a preconfigured keybindings.xml](https://github.com/narfman0/RetroSpy/blob/73b73e6675a3fa985a4be31871730e3cce51a180/keybindings.xml)
  * Open the "keybindings.xml" file in a text editor e.g. Visual Studio Code
    * Uncomment the `binding`
    * Change "l" to "left" or "r" to "right". l does not work for nes!

#### Try it out

You must follow these steps in order to receive the special signal.
You must turn off the nintendo and reset the arduino every time.

1. Ensure the NES is powered off
2. Ensure RetroSpy is not running
3. Reset/power on/plug in the arduino
4. Run RetroSpy
5. Turn on the NES

You should briefly see all controller buttons light up. This is the light of glory, the light of
EZ PB. glhf :D

## WIP syncing TAS and NES

WIP WIP instead of the "home" button starting the TAS, we might observe some ms delay still between
NES and TAS. I woudl take a still camera and determine how many frames it is off by, and make "home"
trigger an autohotkey/autoit script to start the TAS and auto increment X frames, where X is the delay.

There is probably a lot of syncing to be done like NES -> obs capture card latency as well. That will all
have to be accounted for :)