---
layout: post
title:  "All Forts Kabaudio setup"
date:   2019-10-10 22:10:00 -0500
categories: resources allforts forts%
---

### [twitch setup guide](https://www.twitch.tv/videos/490508733)

### [pastebin source](https://pastebin.com/QzgfD7vU)

After a bit more work and research, I have decided to change the jump address to $908D instead of $9071. The main reason is so the top walking Koopa can be killed against the left ? block from the left side, setting its value to #$8D.
So the values we want are now 20 8D 90. Note that from the code:
 
Code at $908C
LDA #$80                ; Music value to stop music playing
STA $04F4               ; Store “stop music” value to $04F4 (Sound_QMusic1)
INC $0727               ; Increment World_Num, i.e go to next world!
JMP $84A0             ; Jump to $84A0 i.e Initialise the world map.
 
If we jump to $908D, then execution starts with the byte $80, which is an unofficial opcode i.e we are ‘byte misaligned’.
$80 is a two byte opcode, and has the effect of a two byte NOP instruction.
So the next instruction to execute is at $908F, which is $F4, again, an unofficial opcode. Thankfully, again, this is a two byte opcode, and has the effect of a two byte NOP instruction.
This means our next byte to execute is $9091, which is our INC $0727 instruction as in the above code.  Execution then continues normally, next code to execute being the JMP $84A0, which is a jump to the “initialise the world map” code. From here the code executes normally, however, due to the ram between $06FF and $0000 excluding the stack ($01xx) not being set to zero which should have occurred at $9057:
 
Code at $9057
LDY #$06                                                       ; Load Y with #$06
JSR Clear_Ram_Through_Zero_Page           ; Jump to subroutine that clears all RAM between $YYFF and $0000, and skips the stack i.e clear $06FF -$0200, and $00FF - $0000
 
Because we skipped this section of code, this is what results in the world map being all corrupted when we jump there. It is the sole reason that the autoscroller can be skipped.
 
Im currently working on a faster setup however the last shell is pixel perfect. It is easier than the any% fastest setup, because of the alignment of the shell as it is thrown.
I will update when I complete another stream and do another highlight.
 
-KabAudio, 5 October 2019 11PM AEST
