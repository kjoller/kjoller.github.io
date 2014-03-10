---
layout: post
title:  "Eightuino Design Goal #3: Cheap!"
date:   2014-03-10 16:26:00
tags: [opensource,electronics]
comments: true
---
This post has been a long time coming, but I wanted to write it up at a
time when I had the time to go into some detail with regards to the choices
I had to make, designing the [Eightuino] as cheaply as possible. The things 
in this post are not innovative, nor can the be considered rocket science. 
They are mainly small tips, which I have discovered doing this project.

To sum it up, the cost of a board can be split into three parts:

- The choice of functionality 
- The price of components
- The price of the PCB

Actually, there is a fourth, the manufacture cost of the boards, but seeing
as this is a DIY product, I will not treat this cost. The more of a challenge
it is, the more fun you get to have, right?

Functionality
=============
If you cut an arduino down to the basics you basically have an Atmel Atmega
microcontoller and some stuff to make it work and some other stuff to talk to
it.

You want to do both, but you can choose the first class ticket, and you can
choose the more economic route. The equivalent of cheating your way along with
a freight train is having a microcontroller on a breadboard, three AA batteries
and a pullup resistor on reset and that's about it. I have tried to seek the
middle ground

I have opted to INCLUDE the following:

* Pull-up resistor on the reset pin AND a reset button
* A voltage regulator for provding a known, steady voltage
* Decoupling capacitors to smooth surges in the power supply
* AVR 6-pin programming header
* A pin row for connecting a USB 2 TTL serial interface
* Optional: A crystal oscillator and load capacitors

I have opted to EXCLUDE the following:
* Dual power supply. The Arduino have dual supply, that is both 3.3v and 5v. 
  Mine only have one voltage regulator
* Built in USB interface.

The arduino and clones usually uses either a FTDI USB interface IC or an
Atmega8u2 (or Atmega16u2) IC for the USB interface these chips alone costs 
between 10 and 30 DKK - which touches the total materials cost for the entire
board. When you have more than one board, you might as well use an external
programmer and/or an external USB serial interface. I already have an AVR 
programmer, so that settles it for me.

Price of components
===================
When buying components, it is certainly not that hard to choose component. You
just find something that has the right qualities - and then you just order it 
from [Mouser] or [Digikey]. Okay, this is simplified and actually not true at all, but
for simple project such as this, it would be relatively easy.

I have opted to try and find parts that is cheaply available from China, that is
available from [Ebay], [AliExpress] or [DealExtreme].

An example was the voltage regulator. Because I wanted to have the option of
going either 3.3V or 5V, I could not use the classic 7805. So I found the
LM1117. But since the through hole version was $0.50, it was kind of expensive.
But the SMD version (SOT-223) was only $0.05, so I decided to be adventurous
and try my first SMD part - It turned out that SOT-223 is an enormous SMD part
and not hard at all to solder, so the decision payed off, and I saved almost
3 Royal Danish Crowns on the voltage regulator alone!

Another example is the Atmega microcontroller. If you don't need the 32Kb of 
memory (and most of the time I do not) or the 16MHz clock (and most of the
time I do not), you can use the Atmega8L (8Kb, 8MHz) as a perfectly good 
replacement for the ususal Atmega328P. The Atmega8L is usually about $1 
compared to the about $2.50 for the Atmgea328P.

The pinouts of the Atmega8L and Atmega328P are the same, so the board can
be used for both, should the need for speed show its face.

Price of the PCB
================
Getting a PCB made is not expensive at all these days, and there are several
services out there, offering small runs for the price of a pizza including
shipping (both the PCBs and the pizza). The common offer is 10pcs PCBs for
$10, if the PCB is less than 5x5cm. 

So to make the PCBs as cheap as possible, the goal is to stay under 5x5cm.
Simple as that!. A 2x3cm costs the same as 5x5cm, feel free to go nuts within
the boundaries.

I have tried both [IteadStudio] and [Elecrow], and [SeeedStudio] is another
service provider - they all use the same factory as far as I have gathered. 
I usually go with Elecrow, because they offer colours other than green without 
extra costs.

Other manufacturers, such as [OSHPark] have other price schemes, where you
pay by area unit ($5 per square inch), and such smaller is cheaper.

Conclusions
===========

* Do not go for more functionality than you need
* Choose a cheaper part, if it can do the job
* Keep your PCB within the constraints of the manufactures price tiers.

Oh, and a word of warning: when shopping cheap, look out for dodgy vendors. I 
have 10 1:1 scale models (non-functioning) of the Attiny2313 to prove it.

[Ebay]: http://ebay.com/
[AliExpress]: http://aliexpress.com/
[DealExtreme]: http://dx.com/
[Mouser]: http://mouser.com/
[Digikey]: http://digikey.com/
[IteadStudio]: http://iteadstudio.com/
[Elecrow]: http://elecrow.com/
[SeeedStudio]: http://seeedstudio.com/
[OSHPark]: http://oshpark.com/
[Eightuino]: /introducing-the-eightuino/

