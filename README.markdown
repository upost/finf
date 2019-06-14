FINF Is Not Forth
=================

Edited by Uwe Post. Based on FINF 0.1.7 by Leandro A. F. Pereira.

Tested on Arduino Nano Clone, builds with Arduino IDE 1.8.9.

Use a serial terminal (i.e. Linux: minicom, Android: Serial USB Terminal), configure to 9600 Baud, 8 Bits, no parity, 1 stop bit.


What is it?
-----------

FINF is a simple implementation for a FORTH-like language for the Arduino platform. It is free software, released under GNU GPL version 2.

Current version weights about 8kB of object code (8.8kB if built with TERMINAL defined), making it suitable even for less beefier Arduinos, such as the ones based on the Atmega168 microcontrollers (even though it runs out of memory quickly and starts to behave weirdly).

See wiki for a brief description of built-in words.


Getting started
---------------

Install FINF on your Arduino using Arduino IDE. Use serial terminal to connect.

Blinky sample
-------------

```
FINF 0.1.8 - 1061 bytes free
>>> words
+ - * / . stk swap dup words drop = negate delay digwrite pinmode dis if else then begin until emit freemem digread analogread analogwrite > auto in out on off relay led pwm reset load save list erase ! @ ? variable e! e@ e? key step mot 
Word count: 
69
>>> begin led on 500 delay led off 500 delay 0 until

```

Advanced samples
----------------
Connect a speaker to ground and pin D4.

Then type this:

```
begin 3 analogread 4 tone 10 delay 0 until
```

You will hear a tone. Touch pin A3 (analog input) and you will hear the tone changing.
Stop with Ctrl+C and `4 notone`

Try this to create noise usind the random generator:

```
begin 2000 rnd 4 tone 0 until
```


