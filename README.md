# Casio CFX/fx BASIC Games (not uploaded yet, please wait)

Games I wrote some time ago for the CASIO CFX-9850GB Plus. Language: CASIO-BASIC, graphics: text mode with non-essential colors. Can run on just about any graphing CASIO with a 128x64 screen (such as fx-9860G series) using automatic conversion within CASIO's [FA-124 program](https://edu.casio.com/forteachers/er/software/).  
In files where minor adjustments are neccessary (removal of color commands if the display is B/W, adding delay loops to keypress routines if the processor is significantly faster), the adjusted version is also provided

## How to connect to calculator

Use CASIO's old but functional [FA-124 program](https://edu.casio.com/forteachers/er/software/) for Windows.  
If your calculator has no USB port, you will need a serial adapter. The official FA-124 cable is $100 so here's an Arduino alternative:

- **USE THIS GUIDE AT YOUR OWN RISK**
- Use an Arduino board such as Uno or Nano with an ATmega processor running at 5V logic levels and dedicated USB-serial adapter chip. Other MCUs might work but they haven't been tested.
- Cut up old stereo headphones to get a 2.5mm (not 3.5"!) jack. It needs to have 3 or 4 contacts to work.
- Use a multimeter's continuity mode to identify which wires go to which contact. From the tip of the jack, we will call them T (*tip*), R (*ring* - first cylinder-shaped contact from the tip), S' (optional second ring used in button/mic headphones, connect with S wire), S (*sleeve* - contact at the base of the jack). It is recommended to solder these on a 3-pin header or breadboard jumpers and add S-R-T labels to them.
- Disable the Arduino's processor. No need to reprogram it if it contains another program. The options are, in order of convenience: - connect RESET pin to ground to keep the chip in a RESET state - remove the chip if it's socketed like on the Uno - short or hold the RESET button for the entirety of operation - flash it with no bootloader and an empty program (not recommended, as you might need an external programmer to revert this!)
- Connect jack S to ground, jack R *via 1kΩ resistor* to Arduino's RX pin and jack T *via 1kΩ resistor* to Arduino's TX pin. *(see notes below)*
- Connect the jack, *then* power up the calculator, then connect the Arduino's USB cable.
- Use Device Manager to find out which serial port number the device is mapped to.
- Select the correct calculator model and serial port in the FA-124 program's settings.
- Follow instructions on how to use the program with your specific model. However, they should be pretty obvious after this point.

#### Notes:

- In a CASIO LINK cable (two 2.5mm jacks, used for communication between calculators), the RX and TX pins are inverted inside the cable for obvious reasons (one calc receives what the other transmits). If you want an adapter that connects to a 2.5mm socket and uses such cable, you'll need to swap RX and TX.
- The reason we are using 1kΩ resistors (the value can probably be up to twice or half as much) between the calc and USB-serial adapter is to reduce short circuit current. Jacks are prone to shorting between contacts when partially inserted, which is why I always connect the jack first and power up the calc and Arduino second. There is also a chance of incorrect RX/TX wiring and the resistors should also save you if that happens. You can omit them at your own risk.   

## TriPeaks / Monochrome version w/throttled input

Clone of Microsoft Solitaire Collection's *TriPeaks* game with the same scoring (1:100). Arrows or F1-F6 to move cursor, up to remove card, down to advance through the bottom deck. Three shuffles at the start, you get another if you clear the board.

        O     O     O
       O O   O J   O O
      J 4 O O     O O O
           7       9 9 Q
                   ^
    SCORE    O→⒑   
     21             

## Logik / Monochrome version

Mastermind with 4 digits. For each digit in your guess:

 - If the digit appears in the same position in the hidden number, it is counted as a hit, otherwise:
 - If the digit appears at least once in another position in the hidden number, **no matter if that digit in the hidden number was already counted**, it counts as a miss.
 - You get the number of hits & misses for your guess displayed. The display is not very tall so you'll likely need to write them down. 

This is a non-standard algorithm (guess `1112` for hidden number `1234` yields 1 hit and 3 misses as opposed to 1 hit and 1 miss) but easy to get used to.

## Snake / Version w/throttled input

Very standard text mode snake in a wrapping 10x7 playfield. No bonus points or anything, really.

## 15Puzzle

Implementation of the classic "15 Puzzle". The CASIO does not have enough power for 2048 to make sense, sadly. Most of the shuffling time is actually spent checking if the permutation is solvable.

## GUESSNUM

My first program, a very simple one. Guess the natural number the calculator thinks between 1 and an adjustable maximum based on less-than/higher-than clues.

# Not games

Also included here: I'm not making another repo for them.

## GCD+LCM

Uses Euler's algorithm to calculate the greatest common denominator & lowest common multiple of two natural numbers.

## PASCAL T / Monochrome version

Draws a colored 64-row Pascal's triangle with a user-set modulo. White pixels represent zeros, orange pixels represent a user-set value, green pixels represent another user-set value and the rest are black. The monochrome version uses pixels only drawn on the left & right instead of colors, breaking the symmetry. 
