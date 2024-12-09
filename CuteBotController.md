### @explicitHints false
# STEM - CuteBot Controller 
## Let's build a robot controller  @showdialog
Let's build a micro:bit project that will drive a CuteBot by sending messages over radio signal.
To help you out, we've created some variables that you will need later: ``||variables: Forwards, Reverse, Left, Right, Stop||``.
```validation.global
# BlocksExistValidator
```
```template
let Forwards = "FORWARDS"
let Reverse = "REVERSE"
let Left = "LEFT"
let Right = "RIGHT"
let Stop = "STOP"
let Direction = "STOP"
```
```blocks
let Forwards = "FORWARDS"
let Reverse = "REVERSE"
let Left = "LEFT"
let Right = "RIGHT"
let Stop = "STOP"
let Direction = "STOP"
```
## Show your micro:bit name 
Let's start by dragging a ``||basic:Basic:show string||`` block into the top of ``||basic:on start||``.
Drag ``||control:Control:device name||`` into to ``||basic:show string||``; this will show your micro:bit's name. 

```blocks
// @highlight
basic.showString(control.deviceName())
let Forwards = "FORWARDS"
let Reverse = "REVERSE"
let Left = "LEFT"
let Right = "RIGHT"
let Stop = "STOP"
let Direction = "STOP"
```
## Set your radio group
Drag a ``||radio:Radio:set group||`` block into ``||basic:on start||``; enter your radio group number. Use a ``||basic:Basic:show string||`` block to show your radio group number. 
```blocks
basic.showString(control.deviceName())
//@highlight
radio.setGroup(1)
//@highlight
basic.showString("1")
let Forwards = "FORWARDS"
let Reverse = "REVERSE"
let Left = "LEFT"
let Right = "RIGHT"
let Stop = "STOP"
let Direction = "STOP"
```
## Add a Loop block to your canvas
To control your CuteBot, drag a ``||loops:Loops:every 500ms||`` block onto your canvas, change the 500ms to 100ms.
```blocks
// @highlight
loops.everyInterval(100, function () {
})
```
## Set direction to stop
Set your ``||variables:Direction||`` to ``||variables:Stop||``. To know which way to send your micro:bit, in the following steps we will check if A, B or A+B are pressed. We will also check if the micro:bit is tilted backwards.
```blocks
loops.everyInterval(100, function () {
// @highlight
let Direction = Stop
})
```
## Check for button A (left)
Drag an ``||logic:if true then||`` block into the ``||loops:every 100ms||`` block. 
Drag a ``||input:button A is pressed||`` block into the ``||logic:if true then||`` block. Drag a ``||variables:set Direction = 0||`` block inside the ``||logic:if||`` statement. Replace the 0 with ``||variables:Left||``.
```blocks
loops.everyInterval(100, function () {
let Direction = Stop
    // @highlight
    if (input.buttonIsPressed(Button.A)) {
        Direction = Left
    }
})
```
## Check for button B (right)
Duplicate the ``||logic:if button A is pressed||`` block (right click, then duplicate) and drag it underneath the ``||logic:if button A is pressed||`` block; change the button to B and the direction to ``||variables:Right||``.
```blocks
loops.everyInterval(100, function () {
let Direction = Stop
    if (input.buttonIsPressed(Button.A)) {
        Direction = Left
    }
    // @highlight
    if (input.buttonIsPressed(Button.B)) {
        Direction = Right
    }
})
```
## Check for button A+B (forwards)
Duplicate the ``||logic:if button B is pressed||`` block (right click, then duplicate) and drag it underneath the ``||logic:if button B is pressed||`` block; change the button to A+B and the direction to ``||variables:Forwards||``.
```blocks
loops.everyInterval(100, function () {
let Direction = Stop
    if (input.buttonIsPressed(Button.A)) {
        Direction = Left
    }
    if (input.buttonIsPressed(Button.B)) {
        Direction = Right
    }
    // @highlight
    if (input.buttonIsPressed(Button.AB)) {
        Direction = Forwards
    }
})
```
## Check for tilt backwards (reverse)
Drag an ``||logic:if true then||`` block into the bottom of the ``||loops:every 100ms||`` block. 
Drag a ``||logic:Logic:0>0||`` comparision block into the ``||logic:if||`` block.
Drag ``||input:Input:rotation||`` into left side of the number comparision and set to ">" 60 (greater than 60).
Drag ``||variables:Variables: set xyz = 0||`` inside the ``||logic:if||`` block and set ``||variables:Direction||`` to ``||variables:Reverse||``.
```blocks
loops.everyInterval(100, function () {
let Direction = Stop
    if (input.buttonIsPressed(Button.A)) {
        Direction = Left
    }
    if (input.buttonIsPressed(Button.B)) {
        Direction = Right
    }
    if (input.buttonIsPressed(Button.AB)) {
        Direction = Forwards
    }
    // @highlight
    if (input.rotation(Rotation.Pitch) > 60) {
    	Direction = Reverse
    }
})
```
## Step 6 - Add radio send "Backwards"
Drag ``||radio:Radio:send string||`` into the if-block and send the value "Backwards" 
```blocks
loops.everyInterval(100, function () {
    if (input.rotation(Rotation.Pitch) > 60) {
        radio.sendString("Backwards")    	
    }
})
```
## Step 7 - Click "+" twice to show an else-if placeholder
Click "+" at the bottom of the if-block twice to show an else-if placeholder 
```blocks
loops.everyInterval(100, function () {
    if (input.rotation(Rotation.Pitch) > 60) {
        radio.sendString("Backwards")
    } else if (true) {
    	
    } else {
    	
    }
})
```
## Step 8 - Add button A+B is pressed to go forwards 
Add ``||input:Input:button A+B is pressed||`` to the else-if and add a ``||radio:Radio:send string||`` block to send "Forwards" 
```blocks
loops.everyInterval(100, function () {
    if (input.rotation(Rotation.Pitch) == 60) {
        radio.sendString("Backwards")
    } else if (input.buttonIsPressed(Button.AB)) {
        radio.sendString("Forwards")
    } else {
    	
    }
})
```
## Step 9 - Add button A is pressed to go left 
Add ``||input:Input:button A is pressed||`` to the else-if and add a ``||radio:Radio:send string||`` block to send "Left" 
```blocks
loops.everyInterval(100, function () {
    if (input.rotation(Rotation.Pitch) > 60) {
        radio.sendString("Backwards")
    } else if (input.buttonIsPressed(Button.AB)) {
        radio.sendString("Forwards")
    } else if (input.buttonIsPressed(Button.A)) {
        radio.sendString("Left")
    
    } else {
    }
})
```
## Step 10 - Add button B is pressed to go right 
Add ``||input:Input:button B is pressed||`` to the else-if and add a ``||radio:Radio:send string||`` block to send "Right" 
```blocks
loops.everyInterval(100, function () {
    if (input.rotation(Rotation.Pitch) > 60) {
        radio.sendString("Backwards")
    } else if (input.buttonIsPressed(Button.AB)) {
        radio.sendString("Forwards")
    } else if (input.buttonIsPressed(Button.A)) {
        radio.sendString("Left")
    } else if (input.buttonIsPressed(Button.B)) {
        radio.sendString("Right")
    
    } else {
    }
})
```
## Step 11 - Complete the if-block by adding the "Stop" radio message 
Complete the if-block by adding a ``||radio:Radio:send string||`` block to send "Stop" 
```blocks
loops.everyInterval(100, function () {
    if (input.rotation(Rotation.Pitch) > 60) {
        radio.sendString("Backwards")
    } else if (input.buttonIsPressed(Button.AB)) {
        radio.sendString("Forwards")
    } else if (input.buttonIsPressed(Button.A)) {
        radio.sendString("Left")
    } else if (input.buttonIsPressed(Button.B)) {
        radio.sendString("Right")
    } else {
        radio.sendString("Stop")
    }
})
```
## Step 12 - Add radio send string "Rainbow" to on logo pressed 
To flash the Cutebot's lights, drag a ``||input:Input:on logo pressed||`` block onto canvas and use ``||radio:Radio:send string||`` to send "Rainbow" 
```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    radio.sendString("RAINBOW")
})
```
## Step 13 - download and test
Click ``|Download|`` to download your code onto your micro:bit to see it working

<script src="https://makecode.com/gh-pages-embed.js"></script><script>makeCodeRender("{{ site.makecode.home_url }}", "{{ site.github.owner_name }}/{{ site.github.repository_name }}");</script>
