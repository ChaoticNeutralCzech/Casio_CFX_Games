# Casio_CFX_Games
Games I wrote some time ago for the CASIO CFX-9850GB Plus. Language: CASIO-BASIC, graphics: text mode with non-essential colors. Can run on just about any graphing CASIO with a 128x64 screen but might need minor adjustments (remove color commands if the display is B/W, add delay loops to keypress routines if the processor is significantly faster)

## TriPeaks

Clone of Microsoft Solitaire Collection's *TriPeaks* game with the same scoring (1:100). Arrows or F1-F6 to move cursor, up to remove card, down to advance through the bottom deck. Three shuffles at the start, you get another if you clear the board.

        O     O     O
       O O   O J   O O
      J 4 O O     O O O
           7       9 9 Q
                   ^
    SCORE    O→⒑   
     21             

## Logik

Mastermind with 4 digits. For each digit in your guess:

 - If the digit appears in the same position in the hidden number, it is counted as a hit, otherwise:
 - If the digit appears at least once in another position in the hidden number, **no matter if that digit in the hidden number was already counted**, it counts as a miss.
 - You get the number of hits & misses for your guess displayed. The display is not very tall so you'll likely need to write them down. 

This is a non-standard algorithm (guess `1112` for hidden number `1234` yields 1 hit and 3 misses) but easy to get used to.

## Snake

Very standard text mode snake in a wrapping 10x7 playfield. No bonus points or anything, really.

## 15Puzzle

Implementation of the classic "15 Puzzle". The CASIO does not have enough power for 2048 to make sense, sadly. Most of the shuffling time is actually spent checking if the permutation is solvable.
