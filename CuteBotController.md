### @explicitHints true
# STEM - CuteBot Controller
## Step 1 - Let's build a micro:bit that can drive our CuteBot 
Let's build a micro:bit project that will drive a CuteBot by sending messages over radio signal.  
Pressing A+B together will send "Forwards"; the A button will send "Left"; the B button will send "Right".  
Tilting your micro:bit towards you will send "Reverse".  
Let's start by showing our micro:bit name.   
Click ``||basic:show string||``
Click ``||control:device name||``
Click ``||radio:set group||``
Click ``||loop:everyInterval||``
```template
//
```
```blocks
basic.showString(control.deviceName())
```
## Step 2 - Set your radio group
Now set your radio group number and show it on start up.
```blocks
basic.showString(control.deviceName())
radio.setGroup(1)
basic.showString("1")
```
## Step 3 - Let's add a Loop and if block
To control our CuteBot we will need a loop-block; inside the loop block we will need an if-block
```blocks
loops.everyInterval(100, function () {
    if (true) {
    	
    }
})
```
## Step 4 - add a number comparer
Drag in number comparer from the Logic menu
```blocks
loops.everyInterval(100, function () {
    if (0 == 0) {
    	
    }
})
```
## Step 5 - add pitch to left side of number comparer
Drag in pitch from Input > ... more and set the comparer to ">" 60 (greater than 60)
```blocks
loops.everyInterval(100, function () {
    if (input.rotation(Rotation.Pitch) > 60) {
    	
    }
})
```
## Step 6 - Add radio send "Backwards"
Drag radio send string into the if-block and send the value "Backwards" 
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
Add button A+B is pressed to the else-if and add a radio send string "Forwards"
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
Add button A is pressed to the else-if and add a radio send string "Left"
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
Add button B is pressed to the else-if and add a radio send string "Right"
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
Complete the if-block by adding radio send string "Stop" 
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
To flash the Cutebot's lights, drag on logo pressed onto canvas and use radio send string to send "Rainbow" 
```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    radio.sendString("RAINBOW")
})
```
## Step 13 - download and test
Download your code onto your micro:bit to see it working

<script src="https://makecode.com/gh-pages-embed.js"></script><script>makeCodeRender("{{ site.makecode.home_url }}", "{{ site.github.owner_name }}/{{ site.github.repository_name }}");</script>
