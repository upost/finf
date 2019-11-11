FINF Is Not Forth (but for Arduino)
===================================

Actively developed by Uwe Post, based on FINF 0.1.7 by Leandro A. F. Pereira.

Tested on Arduino Nano Clone, builds with Arduino IDE 1.8.9.

Run a serial terminal, connect your Arduino and speak Forth!


What is it?
-----------

FINF is an implementation of a FORTH-like language for the Arduino platform with hardware specific additions. It is free software, released under GNU GPL version 2.

Current version weights about 8kB of object code (8.8kB if built with TERMINAL defined), making it suitable even for less beefier Arduinos, such as the ones based on the Atmega168 microcontrollers (even though it runs out of memory quickly and starts to behave weirdly).

See Wiki for a brief description of built-in words.


Getting started
---------------

Install FINF on your Arduino using Arduino IDE. Use serial terminal  (i.e. Linux: minicom, Android: Serial USB Terminal) to connect (configure to 9600 Baud, 8 Bits, no parity, 1 stop bit). At the prompt, type `words`.

```
FINF 0.1.8 - 1061 bytes free
>>> words
+ - * / . stk swap dup words drop = negate delay digwrite pinmode dis if else then begin until emit freemem digread analogread analogwrite > auto in out on off relay led pwm reset load save list erase ! @ ? variable e! e@ e? key step mot 
Word count: 
69
```


Blinky example
--------------
Have the onboard LED blink:

```
FINF 0.1.8 - 1061 bytes free
>>> begin led on 500 delay led off 500 delay 0 until

```

Advanced examples
-----------------
Connect a speaker to ground and pin D4.

Then type this:

```
begin 3 analogread 4 tone 10 delay 0 until
```

You will hear a tone. Touch pin A3 (analog input) and you will hear the tone changing because your body has some electric potential.
Stop with Ctrl+C and then type `4 notone` for silence (or press Reset).

Try this to create noise usind the random generator:

```
begin 2000 rnd 4 tone 0 until
```

Connect a light sensitive resistor and a fixed resistor to ground, Vcc and port A2 (analog in). Connect a LED to port D2 (digital out).
The LED will light up as long as the brightness on the light sensitive resistor is below a certain value (use your finger to shield it from the light).

```
2 out begin 2 analogread 100 > 2 digwrite 0 until
```




More examples to come.

