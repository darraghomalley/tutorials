### @explicitHints false
# STEM - CuteBot Controller 
## Let's build a robot controller  @showdialog
Let's build a micro:bit project that will drive a CuteBot by sending messages over radio signal.
```validation.global
# BlocksExistValidator
```
```template
// @highlight
let A_ButtonIsPressed = "A button IS pressed"
// @highlight
let A_ButtonIsNotPressed = "A button IS NOT pressed"
// @highlight
let B_ButtonIsPressed = "B button IS pressed"
// @highlight
let B_ButtonIsNotPressed = "B button IS NOT pressed"
// @highlight
let Pitch = "Pitch"
// @highlight
let RainbowLights = "RainbowLights"
```
## To help you out, we have added these variables for you  @showdialog
You will drag these onto your canvas later on
```blocks
// @highlight
let A_ButtonIsPressed = "A button IS pressed"
// @highlight
let A_ButtonIsNotPressed = "A button IS NOT pressed"
// @highlight
let B_ButtonIsPressed = "B button IS pressed"
// @highlight
let B_ButtonIsNotPressed = "B button IS NOT pressed"
// @highlight
let RainbowLights = "RainbowLights"
```
## Show your micro:bit name when it starts up!
Let's start by dragging a ``||basic:Basic:show string||`` block into the top of ``||basic:on start||``.
Drag ``||control:Control:device name||`` into to ``||basic:show string||``; this will show your micro:bit's name. 

```blocks
// @highlight
basic.showString(control.deviceName())
let A_ButtonIsPressed = "A button IS pressed"
let A_ButtonIsNotPressed = "A button IS NOT pressed"
let B_ButtonIsPressed = "B button IS pressed"
let B_ButtonIsNotPressed = "B button IS NOT pressed"
let RainbowLights = "RainbowLights"
```
## Set your radio group
Drag a ``||radio:Radio:set group||`` block into ``||basic:on start||``; enter your radio group number.
Use a ``||basic:Basic:show string||`` block to show your radio group number. 
Add a ``||basic:Basic:pause||`` and set ms to 500 and add ``||basic:Basic:clear screen||``
```blocks
basic.showString(control.deviceName())
// @highlight
radio.setGroup(1)
// @highlight
basic.showString("1")
// @highlight
basic.pause(500)
// @highlight
basic.clearScreen()
let A_ButtonIsPressed = "A button IS pressed"
let A_ButtonIsNotPressed = "A button IS NOT pressed"
let B_ButtonIsPressed = "B button IS pressed"
let B_ButtonIsNotPressed = "B button IS NOT pressed"
let RainbowLights = "RainbowLights"
```
## Add a forever block to your canvas, we will use this to know when button A is pressed
To control your CuteBot, drag a ``||basic:Basic:Forever||`` block onto your canvas
```blocks
// @highlight
basic.forever(function () {

})
```
## Add an if true then else block to your forever block
Drag a ``||logic:Logic:if true then else||`` block into your ``||basic:Basic:Forever||`` loop
```blocks

basic.forever(function () {
// @highlight
    if (true) {
    } else {
    }
})
```
## Add code that checks if button A is pressed
Drag a ``||input:Input:button A is pressed||`` block into your if statement
```blocks
basic.forever(function () {
// @highlight
    if (input.buttonIsPressed(Button.A)) {
    } else {
    }
})
```
## Add code to send a radio signal if the A button is pressed
Drag a ``||radio:Radio:send string||`` block into the top of the ``||logic:if||`` block, then drag the ``||variables:Variable:A_ButtonIsPressed||`` variable into the ``||radio:Radio:send string||`` block
```blocks
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
// @highlight
        radio.sendString(A_ButtonIsPressed)
    } else {
    }
})
```
## Add code to send a radio signal if the A button is not pressed
Drag a ``||radio:Radio:send string||`` block into the bottom of the ``||logic:if||`` block, then drag the ``||variables:Variable:A_ButtonIsNotPressed||`` variable into the ``||radio:Radio:send string||`` block
```blocks
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        radio.sendString(A_ButtonIsPressed)
    } else {
// @highlight
        radio.sendString(A_ButtonIsNotPressed)
    }
})
```
## To create a B button forever block, right click the A button forever block and duplicate it
Change the new block so that it works for the B button
```blocks
// @highlight
basic.forever(function () {
    if (input.buttonIsPressed(Button.B)) {
        radio.sendString(B_ButtonIsPressed)
    } else {
        radio.sendString(B_ButtonIsNotPressed)
    }
})
```
## Add a third forever block to your canvas, we will use this to know when your micro:bit is titled backwards
Drag another ``||basic:Basic:Forever||`` block onto your canvas. Tilting your micro:bit backwards will reverse your robot.
Use a ``||radio:Radio:radio send value " "||`` block and drag ``||input:Input:rotation (º) pitch||`` into it.
```blocks
basic.forever(function () {
// @highlight
    radio.sendValue(Pitch, input.rotation(Rotation.Pitch))
})
```

## Add radio send string "Rainbow" to on logo pressed 
To flash the Cutebot's lights, drag a ``||input:Input:on logo pressed||`` block onto canvas and use ``||radio:Radio:send string||`` to send "Rainbow" 
```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    radio.sendString(RainbowLights)
    basic.showString("R")
})
```
## Download and test your code!
Click ``|Download|`` to download your code onto your micro:bit to see it working, or click ``|Next|`` for stretch activities

## If you have time, let's use some pixels to know which way we are sending our CuteBot @showdialog
We can use the ``||led:Led:plot||`` block to turn ON a pixel.
We can use the ``||led:Led:unplot||`` block to turn OFF a pixel.
``||led:plot||`` and ``||led:unplot||`` work like ``||basic:Basic:ShowLeds||`` block; however, they control the pixels on their own.
```blocks
basic.showLeds(`
        # . . . .
        . . . . .
        . . . . .
        . . . . .
        . . . . .
        `)
```

## Let's add plot & unplot to to our button A forever loop
The top left pixel will light up while A is pressed, to turn it on we need ``||led:Led:plot x 0 y 0||`` and to turn it off ``||led:Led:unplot x 0 y 0||``
```blocks
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        radio.sendString(A_ButtonIsPressed)
// @highlight
        led.plot(0, 0)
    } else {
        radio.sendString(A_ButtonIsNotPressed)
// @highlight
        led.unplot(0, 0)
    }
})
```
## Now let's add plot & unplot to our button B forever loop
The top right pixel will light up while B is pressed, to turn it on we need ``||led:Led:plot x 4 y 0||`` and to turn it off we need ``||led:Led:unplot x 4 y 0||``
```blocks
basic.forever(function () {
    if (input.buttonIsPressed(Button.B)) {
        radio.sendString(B_ButtonIsPressed)
// @highlight
        led.plot(4, 0)
    } else {
        radio.sendString(B_ButtonIsNotPressed)
 // @highlight
        led.unplot(4, 0)
    }
})
```
## What happens when you press A and B together?
Both the top left pixel and the top right pixel should light up! For our CuteBot that means go forwards.

## Finally let's add a new forever block to light up a pixel when tilting backwards to reverse our CuteBot
Drag a final ``||basic:Basic:Forever||`` block onto your canvas.
Add an ``||logic:Logic:if true then else||`` block inside the ``||basic:Basic:Forever||`` block
```blocks
// @highlight
basic.forever(function () {
    if (true) {
    	
    } else {
    	
    }
})
```
## Drag a number comparison block into the if statement
Drag a ``||logic:Logic:< 0 = 0 >||`` block into the ``||logic:if else ||`` statement.
```blocks
basic.forever(function () {
 // @highlight
    if (0 == 0) {
    	
    } else {
    	
    }
})
```
## Set the comparison to rotation (º) pitch > 60
Drag ``||input:Input:rotation (º) pitch||`` into the left side of the comparison, set the comparison symbol to ">" and set the right side of comparison to 60
```blocks
basic.forever(function () {
 // @highlight
    if (input.rotation(Rotation.Pitch) > 60) {
    	
    } else {
    	
    }
})
```

## Finally let's add plot & unplot to our rotation / pitch forever block
Use ``||led:Led:plot x 2 y 4||`` to turn on the reverse pixel and ``||led:Led:unplot x 4 y 0||`` to turn it off.
```blocks
basic.forever(function () {
    if (input.rotation(Rotation.Pitch) > 60) {
 // @highlight
        led.plot(2, 4)
    } else {
 // @highlight
        led.unplot(2, 4)
    }
})
```
## Download and test your stretch exercise
Click ``|Download|`` to download your code onto your micro:bit to see it working
<script src="https://makecode.com/gh-pages-embed.js"></script><script>makeCodeRender("{{ site.makecode.home_url }}", "{{ site.github.owner_name }}/{{ site.github.repository_name }}");</script>
