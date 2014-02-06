---
layout: post
title:  "Eightuino Design Goal #1: DIY friendliness"
date:   2014-02-06 20:07:00
tags: [opensource,electronics]
comments: true
---
In this and the next two posts, I will outline what I understand by the
design goals of the [Eightuino]. The first goal is that it should be
"DIY friendly".

Although the Eightuino in this iteration will be almost exclusively
through-hole, this is NOT what is meant by DIY-friendly. The hole thing
stems from the fact that the otherwise immensively talented people at
Arduino made ONE irritating mistake when designing the layout of the 
Arduino:

On the one side of the board, the gap between the two rows of headers
is a non-standard 0.16". This makes it necessary to use special
"proto-shields" instead of regular 0.1" perfboard when hacking something on top
of it. And protoshields are more expensive than perfboards.

So the Eightuino will definitely have to use a 0.1" pin-spacing. No discussion!

So that is the spacing between the individual pins. But what about the space
between rows? Well, seeing as I personally have about 50-60 pieces 5x7cm 
perfboards lying around, how about I make the Eightuino fit these? They have
18 holes across, making the distance from one side to the other 1.7". So that
is now the official row spacing on the Eightuino. 

All this do, however, break compatibility with existing Arduino Shields, and
an Eightuino User (that is, I) will not be able to share my shield-designs
directly with non-eightuino users. Well, the Eightuino main purpose is home 
DIY use and for hacking together something on a perfboard, not for 
mass-producing pcb-based shields.

Does this make sense? I think so :-)

[Eightuino]: /introducing-the-eightuino/
