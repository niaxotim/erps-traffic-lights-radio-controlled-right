### @activities true
### @explicitHints true

# ERPS STEM WEEK :: Traffic Lights - Radio Controlled - Right

## Introduction
### Introduction Step @unplugged
In this challenge, we are going to use two traffic lights, with radio controls to alternate traffic light sequences. This will require two BBC micro:bits!  
The code in this tutorial will be for one traffic light, with code in the paired tutorial being for the other light.
This form of radio control will be using a 'passing a token method' of control system.  
This code is for what we will call the 'right' traffic light. **Please read the tutorial on the 'left' lights first, and follow the instructions.**

## Basic Radio Receiver
### Step 1
We need to set up the receiving traffic lights. We will need to program this into the second micro:bit.  
Like at the start of the previous code, we need to indicate which BBC micro:bit this is and set the radio group. Add the ``||radio:set group||`` block to the ``||basic.onStart||`` section and set its group to match the one in the left editor (we used 1 in our example). 

#### ~ tutorialhint
```blocks
radio.setGroup(1)
```
