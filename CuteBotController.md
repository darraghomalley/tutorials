### @explicitHints false
# STEM - CuteBot Controller 
## Let's build a robot controller  @showdialog
Let's build a micro:bit project that will drive a CuteBot by sending messages over radio signal.
```validation.global
# BlocksExistValidator
```
```template
//
```
## Show your micro:bit name 
Let's start by dragging a ``||basic:Basic:show string||`` block into the top of ``||basic:on start||``.
Drag ``||control:Control:device name||`` into to ``||basic:show string||``; this will show your micro:bit's name. 

```blocks
// @highlight
basic.showString(control.deviceName())
```
## Set your radio group
Drag a ``||radio:Radio:set group||`` block into ``||basic:on start||``; enter your radio group number. Use a ``||basic:Basic:show string||`` block to show your radio group number. 
```blocks
basic.showString(control.deviceName())
// @highlight
radio.setGroup(1)
// @highlight
basic.showString("1")
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
    if (true) {
}
})
```
## Set direction to stop
Set your ``||variables:Direction||`` to ``||variables:Stop||``. To know which way to send your micro:bit, in the following steps we will check if A, B or A+B are pressed. We will also check if the micro:bit is tilted backwards.
```blocks
  loops.everyInterval(100, function () {
// @highlight
    if (0 == 0) {
}
})
```
## Set direction to stop
Set your ``||variables:Direction||`` to ``||variables:Stop||``. To know which way to send your micro:bit, in the following steps we will check if A, B or A+B are pressed. We will also check if the micro:bit is tilted backwards.
```blocks
  loops.everyInterval(100, function () {
// @highlight
    if (input.rotation(Rotation.Pitch) > 60) {
}
})
```
## Set direction to stop
Set your ``||variables:Direction||`` to ``||variables:Stop||``. To know which way to send your micro:bit, in the following steps we will check if A, B or A+B are pressed. We will also check if the micro:bit is tilted backwards.
```blocks
  loops.everyInterval(100, function () {

    if (input.rotation(Rotation.Pitch) > 60) {
            // @highlight
        basic.showLeds(`
            . . . . .
            . . . . .
            # . . . #
            . # . # .
            . . # . .
            `)
        }
})
```
## Check for button A (left)
Drag an ``||logic:if true then||`` block into the ``||loops:every 100ms||`` block. 
Drag a ``||input:button A is pressed||`` block into the ``||logic:if true then||`` block. Drag a ``||variables:set Direction = 0||`` block inside the ``||logic:if||`` statement. Replace the 0 with ``||variables:Left||``.
```blocks
  loops.everyInterval(100, function () {
// @highlight
    if (input.rotation(Rotation.Pitch) > 60) {
        basic.showLeds(`
            . . . . .
            . . . . .
            # . . . #
            . # . # .
            . . # . .
            `)
            // @highlight
        radio.sendString("B")
}
})
```
## Check for button B (right)
Duplicate the ``||logic:if button A is pressed||`` block (right click, then duplicate) and drag it underneath the ``||logic:if button A is pressed||`` block; change the button to B and the direction to ``||variables:Right||``.
```blocks
loops.everyInterval(100, function () {
    if (input.rotation(Rotation.Pitch) > 60) {
        basic.showLeds(`
            . . . . .
            . . . . .
            # . . . #
            . # . # .
            . . # . .
            `)
        radio.sendString("B")
    } else if (false) {
    	
    } else {
    	
    }
})
```
## Check for button A+B (forwards)
Duplicate the ``||logic:if button B is pressed||`` block (right click, then duplicate) and drag it underneath the ``||logic:if button B is pressed||`` block; change the button to A+B and the direction to ``||variables:Forwards||``.
```blocks
loops.everyInterval(100, function () {
    if (input.rotation(Rotation.Pitch) > 60) {
        basic.showLeds(`
            . . . . .
            . . . . .
            # . . . #
            . # . # .
            . . # . .
            `)
        radio.sendString("B")
    } else if (input.buttonIsPressed(Button.AB)) {
    	
    } else {
    	
    }
})
```
## Check for tilt backwards (reverse)
Test some stuff out
```blocks
loops.everyInterval(100, function () {
    if (input.rotation(Rotation.Pitch) > 60) {
        basic.showLeds(`
            . . . . .
            . . . . .
            # . . . #
            . # . # .
            . . # . .
            `)
        radio.sendString("B")
    } else if (input.buttonIsPressed(Button.AB)) {
    // @highlight
    basic.showLeds(`
            . . # . .
            . # . # .
            # . . . #
            . . . . .
            . . . . .
            `)
        // @highlight
        radio.sendString("F")
    } else {
    	
    }
})
```
## Add radio send "Forwards"
Drag ``||radio:Radio:send string||`` into the if-block and send the value "Backwards" 
```blocks
loops.everyInterval(100, function () {
    if (input.rotation(Rotation.Pitch) > 60) {
        basic.showLeds(`
            . . . . .
            . . . . .
            # . . . #
            . # . # .
            . . # . .
            `)
        radio.sendString("B")
    } else if (input.buttonIsPressed(Button.AB)) {
    // @highlight
    basic.showLeds(`
            . . # . .
            . # . # .
            # . . . #
            . . . . .
            . . . . .
            `)
        // @highlight
        radio.sendString("F")
    } else if (false) {
    	
    } else {
    	
    }
})
```
## Add radio send "Forwards"
Drag ``||radio:Radio:send string||`` into the if-block and send the value "Backwards" 
```blocks
loops.everyInterval(100, function () {
    if (input.rotation(Rotation.Pitch) > 60) {
        basic.showLeds(`
            . . . . .
            . . . . .
            # . . . #
            . # . # .
            . . # . .
            `)
        radio.sendString("B")
    } else if (input.buttonIsPressed(Button.AB)) {
    // @highlight
    basic.showLeds(`
            . . # . .
            . # . # .
            # . . . #
            . . . . .
            . . . . .
            `)
        // @highlight
        radio.sendString("F")
    } else if (input.buttonIsPressed(Button.A)) {
    	
    } else {
    	
    }
})
```
## Add radio send "Left"
Drag ``||radio:Radio:send string||`` into the if-block and send the value "Backwards" 
```blocks
loops.everyInterval(100, function () {
    if (input.rotation(Rotation.Pitch) > 60) {
        basic.showLeds(`
            . . . . .
            . . . . .
            # . . . #
            . # . # .
            . . # . .
            `)
        radio.sendString("B")
    } else if (input.buttonIsPressed(Button.AB)) {
    // @highlight
    basic.showLeds(`
            . . # . .
            . # . # .
            # . . . #
            . . . . .
            . . . . .
            `)
        // @highlight
        radio.sendString("F")
    } else if (input.buttonIsPressed(Button.A)) {
    	 // @highlight
    basic.showLeds(`
            . . # . .
            . # . . .
            # . . . .
            . # . . .
            . . # . .
            `)
        // @highlight
        radio.sendString("L")
    } else {
    	
    }
})
```
## Add radio send "Left"
Drag ``||radio:Radio:send string||`` into the if-block and send the value "Backwards" 
```blocks
loops.everyInterval(100, function () {
    if (input.rotation(Rotation.Pitch) > 60) {
        basic.showLeds(`
            . . . . .
            . . . . .
            # . . . #
            . # . # .
            . . # . .
            `)
        radio.sendString("B")
    } else if (input.buttonIsPressed(Button.AB)) {
    // @highlight
    basic.showLeds(`
            . . # . .
            . # . # .
            # . . . #
            . . . . .
            . . . . .
            `)
        // @highlight
        radio.sendString("F")
    } else if (input.buttonIsPressed(Button.A)) {
    	 // @highlight
    basic.showLeds(`
            . . # . .
            . # . . .
            # . . . .
            . # . . .
            . . # . .
            `)
        // @highlight
        radio.sendString("L")
    } else if (false) {
    	
    } else {
    	
    }
})
```
## Click + to add an else if
Drag ``||radio:Radio:send string||`` into the if-block and send the value "Backwards" 
```blocks
loops.everyInterval(100, function () {
    if (input.rotation(Rotation.Pitch) > 60) {
        basic.showLeds(`
            . . . . .
            . . . . .
            # . . . #
            . # . # .
            . . # . .
            `)
        radio.sendString("B")
    } else if (input.buttonIsPressed(Button.AB)) {
    // @highlight
    basic.showLeds(`
            . . # . .
            . # . # .
            # . . . #
            . . . . .
            . . . . .
            `)
        // @highlight
        radio.sendString("F")
    } else if (input.buttonIsPressed(Button.A)) {
    	 // @highlight
    basic.showLeds(`
            . . # . .
            . # . . .
            # . . . .
            . # . . .
            . . # . .
            `)
        // @highlight
        radio.sendString("L")
    } else if (input.buttonIsPressed(Button.B)) {
    	
    } else {
    	
    }
})
```
## Add radio send Right
Drag ``||radio:Radio:send string||`` into the if-block and send the value "Backwards" 
```blocks
loops.everyInterval(100, function () {
    if (input.rotation(Rotation.Pitch) > 60) {
        basic.showLeds(`
            . . . . .
            . . . . .
            # . . . #
            . # . # .
            . . # . .
            `)
        radio.sendString("B")
    } else if (input.buttonIsPressed(Button.AB)) {
    // @highlight
    basic.showLeds(`
            . . # . .
            . # . # .
            # . . . #
            . . . . .
            . . . . .
            `)
        // @highlight
        radio.sendString("F")
    } else if (input.buttonIsPressed(Button.A)) {
    	 // @highlight
    basic.showLeds(`
            . . # . .
            . # . . .
            # . . . .
            . # . . .
            . . # . .
            `)
        // @highlight
        radio.sendString("L")
    } else if (input.buttonIsPressed(Button.B)) {
    	    	 // @highlight
    basic.showLeds(`
            . . # . .
            . . . # .
            . . . . #
            . . . # .
            . . # . .
            `)
        // @highlight
        radio.sendString("R")
    } else {
    	
    }
})
```
## Add radio send Stop
Drag ``||radio:Radio:send string||`` into the if-block and send the value "Backwards" 
```blocks
loops.everyInterval(100, function () {
    if (input.rotation(Rotation.Pitch) > 60) {
        basic.showLeds(`
            . . . . .
            . . . . .
            # . . . #
            . # . # .
            . . # . .
            `)
        radio.sendString("B")
    } else if (input.buttonIsPressed(Button.AB)) {
    // @highlight
    basic.showLeds(`
            . . # . .
            . # . # .
            # . . . #
            . . . . .
            . . . . .
            `)
        // @highlight
        radio.sendString("F")
    } else if (input.buttonIsPressed(Button.A)) {
    	 // @highlight
    basic.showLeds(`
            . . # . .
            . # . . .
            # . . . .
            . # . . .
            . . # . .
            `)
        // @highlight
        radio.sendString("L")
    } else if (input.buttonIsPressed(Button.B)) {
    basic.showLeds(`
            . . # . .
            . . . # .
            . . . . #
            . . . # .
            . . # . .
            `)
        radio.sendString("R")
    } else {
    // @highlight
        radio.sendString("S")    	
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
