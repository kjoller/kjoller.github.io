---
layout: post
title:  "Eightuino - Why, Oh, Why?"
date:   2014-02-12 8:32:00
tags: [opensource,electronics]
comments: true
---
There have been some comments on [Elektronik-forum], suggesting other ways
of obtaining a cheap arduino(-clone), instead of doing the work of designing
the thing yourself. So I feel that I need to explain myself. To sum it up, it 
as a matter of a few small adjustments, but mostly the learning experience
of designing a board.

I have been suggested these three methods:
- A chinese clone - basically a 1-to-1 chinese copy
- The [Nanino] - one sided home-etchable FTDI-less board
- The [JEENode] - A stick-thingy with 868MHz RF data transmission

And these are all good suggestions, although the first one is a bit dodgy, 
especially when the copies still have the Arduino logo on it, while not
being produced anywhere near Italy. In fact, I own two chinese copies, one
of the Arduino Leonardo and one of the Arduino Mega.

The nanino is pretty much what I was looking for, except for the pin-spacing
issue, which I mentioned in the [previous post]. And I am not currently doing
home etching of copper. When I take this up, I will definitely make a try of
the Nanino

The JEENode is also great. It has a reasonable pin layout, and the RF thing
looks interesting. But I currently need the RF, and
the while the slim boards a great for breadboards, I like my shields to have
the pins on the sides, not in the middle. They sell empty boards for €5.00, 
which I may try when I get an idea for an RF project.

So I need something that is cheap (Nanino), have a reasonable pin-spacing 
(JEENode) and is good for perfboard shields (??). These are my needs for the
product itself. So I will make it myself. 

I am sure that someone somewhere have built a board that meets my needs 
(almost) perfectly and probably at a reasonable price. But I am also (mainly)
doing this for trying to go through the proces of designing a usable board, 
and discovering all the small pitfalls, which is not apparently clear when
looking at guides on the internet and videos on YouTube.

Stay tuned (still) for the "Designing on a cheap"-post.

[Elektronik-forum]: http://elektronik-forum.dk
[Nanino]: http://vonkonow.com/wordpress/2012/10/nanino-the-diy-friendly-arduino/
[JEENode]: http://www.digitalsmarties.net/products/jeenode