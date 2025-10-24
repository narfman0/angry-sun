---
layout: post
title:  "Early Hammer"
date:   2018-11-14 17:44:50 -0700
categories: notes eh earlyhammer early hammer
---

## [mfp explanation video](https://youtu.be/2syj3j0Ye_E)

## [Early hammer (or4ng33xp0)]({{ site.baseurl }}{% link pages/early-hammer-or4ng33xp0.md %}) [src](http://smb3.bf0.org/)

## [smb3rngchk (or4ng33xp0)]({{ site.baseurl }}{% link assets/notes/smb3rngchk_output.txt %})

or4ng33xp0 made a tool to check the rng results every level. This is how the frames were identified
to create an optimal TAS.

The RNG algorithm (LSFR) was reverse engineered and reimplemnted in c, and the
minimum amount of other game logic was reimplemented as well to try to
simulate the frames.

NBote: this does not count lag frames either, so the runner is expected to figure
out how to avoid that.

## [Early hammer console manipulation (narfman0)]({{ site.baseurl }}{% link pages/early-hammer-console.md %})
