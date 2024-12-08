### @explicitHints true
# STEM - CuteBot Controller
## Step ... - ... 
Let's build a micro:bit project that will drive a CuteBot by sending messages over radio signal.
To help you out, we've created some Variables that you will need later: ``||variables:Forwards, Left, Right, etc.||``. 
```template
let Direction = "STOP"
let Forwards = "FORWARDS"
let Reverse = "REVERSE"
let Left = "LEFT"
let Right = "RIGHT"
let Stop = "STOP"
```
```blocks
let Direction = "STOP"
let Forwards = "FORWARDS"
let Reverse = "REVERSE"
let Left = "LEFT"
let Right = "RIGHT"
let Stop = "STOP"
```
## Step ... - ... 
Let's start by dragging a ``||basic:Basic:show string||`` block into the top of ``||basic:on start||``.
Now let's drag ``||control:Control:device name||`` into to ``||basic:show string||``; this will show our micro:bit's name. 
```blocks
basic.showString(control.deviceName())
let Direction = "STOP"
let Forwards = "FORWARDS"
```

## Step ... - ...
Now add ``||radio:Radio:set group||`` ``||basic:on start||``; this will set your radio group number. Also, show your radio group number using ``||basic:Basic:show string||``. 
```blocks
basic.showString(control.deviceName())
radio.setGroup(1)
basic.showString("1")
let Direction = "STOP"
let Forwards = "FORWARDS"
```
## Step ... - Let's add a Loop block
To control your CuteBot, drag a ``||loops:Loops:every 500ms||`` block onto your canvas, change the 500ms to 100ms.
```blocks
loops.everyInterval(100, function () {
})
```
## Step ... - Let's set our direction to stop
First thing to do is to set ``||variables:Direction||`` to ``||variables:Stop||``. In the following steps we will check if A, B or A+B are pressed. We will also check if the micro:bit is tilted backwards.
```blocks
loops.everyInterval(100, function () {
let Direction = Stop
})
```
## Step ... - Let's create the check for button A
Drag an ``||logic:if true then||`` block into the ``||loops:every 100ms||`` block. 
Drag a ``||input:button A is pressed||`` block into the ``||logic:if true then||`` block. Drag a ``||variables:set Direction = 0||`` block inside the ``||logic:if||`` statement. Replace the 0 with ``||variables:Left||``.
```blocks
loops.everyInterval(100, function () {
let Direction = Stop
    if (input.buttonIsPressed(Button.A)) {
        Direction = Left
    }
})
```
## Step ... - Let's create the check for button B
Duplicate the ``||logic:if button A is pressed||`` block (right click, then duplicate) and drag it underneath the ``||logic:if button A is pressed||`` block; change the button to B and the direction to ``||variables:Right||``.
```blocks
loops.everyInterval(100, function () {
let Direction = Stop
    if (input.buttonIsPressed(Button.A)) {
        Direction = Left
    }
    if (input.buttonIsPressed(Button.B)) {
        Direction = Right
    }
})
```
## Step ... - Let's create the check for button A+B
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
    if (input.buttonIsPressed(Button.AB)) {
        Direction = Forwards
    }
})
```
```
## Step 4 - add a number comparision
Drag a ``||logic:Logic:0=0||`` block into the if-block 
```blocks
loops.everyInterval(100, function () {
    if (0 == 0) {
    	
    }
})
```
## Step 5 - add pitch to left side of number comparision
Drag ``||input:Input:rotation||`` into left side of the number comparision and set to ">" 60 (greater than 60)
```blocks
loops.everyInterval(100, function () {
    if (input.rotation(Rotation.Pitch) > 60) {
    	
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
