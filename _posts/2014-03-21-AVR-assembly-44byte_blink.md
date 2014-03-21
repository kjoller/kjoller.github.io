---
layout: post
title:  "AVR Assembly - The 44-byte blink"
date:   2014-03-21 13:47:00
tags: [opensource,electronics]
comments: true
---
For the past week, I have been looking into assembler programming, specifically
for the AVR series. I have really been enjoying [Gerhard Schmidt's AVR assembler
tutorial][avr-tutorial], which seems very thorough.

I tried to implement the blink example, and maybe went a little overboard.
The usual reasons for using assembler programming instead of C is optimizing
timing and/or program size. My results: the final program is 44 bytes in binary
form, and each led change is (or should be) exactly 16 million cycles, which is
one second on a 16MHz clock. The program can of course be modified for other
clock speeds and blinking intervals - up to 65535 millisecond per blink.

This is compared to the arduino blink example, which is 1084 bytes and precise
only to the millisecond (If I remember correctly).

I am totally new in assembler programming, and if you find a mistake, please
tell me! 

I have ordered some attiny13a's, and made some small development boards for
them. But more on that later!

The code:

```asm
; My first piece of assembler code. It is made to mimic the blink
; example from the Arduino environment. The arduino example compiles
; to around 1Kb - this is 44 bytes. And should be very 
; precise in the timing.
.nolist;
.include "m88def.inc";
.list;


; SETTING CLOCK SPEED - currently at 16 MHz
.equ clockCyclesPerMilliSecond = 16*1000
; The delay to put between blinks in milliseconds
.equ delayMilliseconds = 1000
; The direction register, the port and the bit to set the pin of the
; LED to flash
; Currently at PB5 (Arduino pin 13)
.equ DDR = DDRB
.equ PORT = PORTB
.equ BIT = 5

; SETTING UP REGISTERS
.DEF my_register = R16

; Not sure if this is needed... It works without it.
rjmp	setup

; setup
setup:
    SBI     DDR,BIT         ; Set pin to output

loop:
    sbi     PORT,BIT        ; 2 cycles - set pin HIGH
    rcall   Delay           ; 3 cycles (the call itself) 
    cbi     PORT,BIT        ; 2 cycles - set pin LOW
    rcall   Delay           ; 3 cycles (the call itself)
    rjmp    loop            ; 2 cycles (the jump itself) - repeat
    
Delay:
    nop
    ; Delay consists of two loops - the inner loop loops for a
    ; millisecond, the outer counts the number of milliseconds-
    ; From every inner loop, there is subtracted the number of 
    ; cycles to complete the outer loop (8). From the first time, there
    ; is also subtracted the number of cycles to call, setup and return
    ; from the subroutine as well as the cycles for switching the pin,
    ; half of the rjmp command and the nop in the start of this function
    
    ; inner loop : 4 cycles
    ; outer loop : 8 cycles
    ; pin switching, calling, returning and looping : 16 cycles
    
    ; Since precision is made by cutting the number of times the
    ; inner loop runs, it is important that the number of cycles
    ; in the outer loop and the one-time-fluff is divisble by 4.
    
    ldi     ZH,HIGH((clockCyclesPerMilliSecond-8-16)/4)
    ldi     ZL,LOW((clockCyclesPerMilliSecond-8-16)/4)
    ; A lot of nops and grief could be saved by only supporting a 
    ; maximum of 255 millisecond delay.
    ldi     YL,LOW(delayMilliseconds)
    ldi     YH,HIGH(delayMilliseconds)
    
    delayloop:
            sbiw    ZL, 1       ; 2 cycles
            brne    delayloop   ; 2 cycles
        
        sbiw    YL,1                                     ; 2 cycles
        ldi     ZH,HIGH((clockCyclesPerMilliSecond-8)/4) ; 1 cycle
        ldi     ZL,LOW((clockCyclesPerMilliSecond-8)/4)  ; 1 cycle
        nop ; added to make a number of cycles divisible by 4 1 cycle  
        nop ; added to make a number of cycles divisble by 4  1 cycle
        brne    delayloop                                ; 2 cycles
   
    nop ; added to make a number of cycles divisible by 4 ; 1 cycle
    ret ;                                                   3 cycles
``` 

[avr-tutorial]: http://www.avr-asm-tutorial.net/
