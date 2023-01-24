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
### Step 2
When the code starts, we want our trafficl light to be on "Red".  Add a ``||Kitronik_STOPbit.Make Traffic Light state||`` block after ``||radio:set group||`` and set it to ``||Kitronik_STOPbit.Stop||``.

#### ~ tutorialhint
```blocks
radio.setGroup(1)
Kitronik_STOPbit.trafficLightState(Kitronik_STOPbit.LightStates.Stop)
```

### Step 3
Now our code is ready to receive messages.  
From the ``||radio:Radio||`` category, drag in the ``||radio:on radio receivedString||`` block - this will have a text input within the block.

#### ~ tutorialhint
```blocks
radio.onReceivedString(function (receivedString) {
})
```

### Step 4
Within the ``||radio:on radio receivedString||`` block, we need to check the received message is what we are expecting. If the message is something we know about we can handle it - we call the code that does something a handler.  
Add an ``||logic:if||`` block inside the block and check the received message is "Start Sequence". Place an ``||logic:" " = " "||`` compare block into the ``||logic:if||`` statement. From the ``||radio:on radio receivedString||``, drag ``||variables:receivedString||`` into the first text section, and then type "Start Sequence" into the comparison text box. (**Note:** Make sure the spelling and letter cases are identical to the sent message).

#### ~ tutorialhint
```blocks
radio.onReceivedString(function (receivedString) {
    if (receivedString == "Start Sequence") {
    	
    }
})
```

### Step 5
Next, create a variable called ``||variables:Start_Lights||``, and inside the ``||logic:if||`` section, ``||variables:set Start_Lights to||`` ``||logic:true||``.

#### ~ tutorialhint
```blocks
radio.onReceivedString(function (receivedString) {
    if (receivedString == "Start Sequence") {
        Start_Lights = true
    }
})
```

### Step 6
Now in the ``||basic:forever||`` loop, add an ``||logic:if||`` block which will be checking whether ``||variables:Start_Lights||`` ``||logic:= true||``.

#### ~ tutorialhint
```blocks
basic.forever(function () {
    if (Start_Lights == true) {
    	
    }
})
```

### Step 7
Inside this ``||logic:if||`` bracket, create the traffic light sequence. At the start of our code, we set the light to be at "Stop" already, so do not include that again.  
Our sequence will be shifted by one and goes "Get ready" **->** "Go" **->** "Ready to stop" **->** "Stop". Add this sequence, along with the required ``||basic:pauses||`` at the start and inbetween each step.

#### ~ tutorialhint
```blocks
basic.forever(function () {
    if (Start_Lights == true) {
        basic.pause(2000)
        Kitronik_STOPbit.trafficLightState(Kitronik_STOPbit.LightStates.GetReady)
        basic.pause(500)
        Kitronik_STOPbit.trafficLightState(Kitronik_STOPbit.LightStates.Go)
        basic.pause(2000)
        Kitronik_STOPbit.trafficLightState(Kitronik_STOPbit.LightStates.ReadyToStop)
        basic.pause(1000)
        Kitronik_STOPbit.trafficLightState(Kitronik_STOPbit.LightStates.Stop)
    }
})
```

## Sending Messages
### Step 8
We added (on the other traffic light) two blocks for changing the variable ``||variables:Start_Lights||`` so that it does not run the traffic light code again, and to trigger the other to start.  
Insert ``||variables:set Start_Lights to||`` ``||logic:false||`` after the light sequence, and then add a ``||radio:send string||`` with "Start Sequence" after this as well.

#### ~ tutorialhint
```blocks
basic.forever(function () {
    if (Start_Lights == true) {
        basic.pause(2000)
        Kitronik_STOPbit.trafficLightState(Kitronik_STOPbit.LightStates.GetReady)
        basic.pause(500)
        Kitronik_STOPbit.trafficLightState(Kitronik_STOPbit.LightStates.Go)
        basic.pause(2000)
        Kitronik_STOPbit.trafficLightState(Kitronik_STOPbit.LightStates.ReadyToStop)
        basic.pause(1000)
        Kitronik_STOPbit.trafficLightState(Kitronik_STOPbit.LightStates.Stop)
        Start_Lights = false
        radio.sendString("Start Sequence")
    }
})
```

### Step 8
Connect your second BBC micro:bit and click ``|Download|`` to transfer your code.  
Once programmed, press `||input:button A||`` on the other traffic light and see if they alternate traffic light sequences.

### Traffic Light Tutorial Complete @unplugged
Great work! Hopefully now both of your traffic lights work, and show alternate sequences!  Whew, that was a tricky one!
Way to go! ;)
![Great job](https://raw.githubusercontent.com/niaxotim/erps-traffic-lights-radio-controlled-right/master/assets/great_job.png)
