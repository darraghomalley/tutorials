### @explicitHints false
# STEM - CuteBot Controller 
## Let's build a robot controller  @showdialog
Let's build a micro:bit project that will drive a CuteBot by sending messages over radio signal.
```validation.global
# BlocksExistValidator
```
```template
// @highlight
let A_button_IS_pressed = "A button IS pressed"
// @highlight
let A_button_IS_NOT_pressed = "A button IS NOT pressed"
// @highlight
let B_button_IS_pressed = "B button IS pressed"
// @highlight
let B_button_IS_NOT_pressed = "B button IS NOT pressed"
// @highlight
let RainbowLights = "RainbowLights"
```
## To help you out later on, we have added these variables for you  @showdialog
You will drag these onto your canvas later on
```blocks
// @highlight
let A_button_IS_pressed = "A button IS pressed"
// @highlight
let A_button_IS_NOT_pressed = "A button IS NOT pressed"
// @highlight
let B_button_IS_pressed = "B button IS pressed"
// @highlight
let B_button_IS_NOT_pressed = "B button IS NOT pressed"
// @highlight
let RainbowLights = "RainbowLights"
```
## Show your micro:bit name when it starts up!
Let's start by dragging a ``||basic:Basic:show string||`` block into the top of ``||basic:on start||``.
Drag ``||control:Control:device name||`` into to ``||basic:show string||``; this will show your micro:bit's name. 

```blocks
// @highlight
basic.showString(control.deviceName())
let A_button_IS_pressed = "A button IS pressed"
let A_button_IS_NOT_pressed = "A button IS NOT pressed"
let B_button_IS_pressed = "B button IS pressed"
let B_button_IS_NOT_pressed = "B button IS NOT pressed"
let RainbowLights = "RainbowLights"
```
## Set your radio group
Drag a ``||radio:Radio:set group||`` block into ``||basic:on start||``; enter your radio group number.
Use a ``||basic:Basic:show string||`` block to show your radio group number. 
Add a ``||basic:Basic:pause||`` and set ms to 300 and add ``||basic:Basic:clear screen||``
```blocks
basic.showString(control.deviceName())
// @highlight
radio.setGroup(1)
// @highlight
basic.showString("1")
// @highlight
basic.pause(300)
// @highlight
basic.clearScreen()
let A_button_IS_pressed = "A button IS pressed"
let A_button_IS_NOT_pressed = "A button IS NOT pressed"
let B_button_IS_pressed = "B button IS pressed"
let B_button_IS_NOT_pressed = "B button IS NOT pressed"
let RainbowLights = "RainbowLights"
```
## Add a forever block to your canvas, we will use this to know when button A is pressed
To control your CuteBot, drag a ``||basic:Basic:Forever||`` block onto your canvas
```blocks
// @highlight
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        radio.sendString(A_button_IS_pressed)
    } else {
        radio.sendString(A_button_IS_NOT_pressed)
    }
})
```
## Add another forever block to your canvas, we will use this to know when button B is pressed
Drag another ``||basic:Basic:Forever||`` block onto your canvas
```blocks
basic.forever(function () {
    if (input.buttonIsPressed(Button.B)) {
        radio.sendString(B_button_IS_pressed)
    } else {
        radio.sendString(B_button_IS_NOT_pressed)
    }
})
```
## Add a third forever block to your canvas, we will use this to know when your micro:bit is titled backwards
Drag another ``||basic:Basic:Forever||`` block onto your canvas. Tilting your micro:bit backwards will reverse your robot
```blocks
basic.forever(function () {
// @highlight
    radio.sendValue("Pitch", input.rotation(Rotation.Pitch))
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
## download and test
Click ``|Download|`` to download your code onto your micro:bit to see it working, or click ``|Next|`` for stretch activities

## Let's use some pixels to know which way we are sending our CuteBot  @showdialog
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
The top left pixel will light up while A is pressed
```blocks
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        radio.sendString(A_button_IS_pressed)
// @highlight
        led.plot(0, 0)
    } else {
        radio.sendString(A_button_IS_NOT_pressed)
// @highlight
        led.unplot(0, 0)
    }
})
```
## Now let's add plot & unplot to our button B forever loop
The top left pixel will light up while A is pressed
```blocks
basic.forever(function () {
    if (input.buttonIsPressed(Button.B)) {
        radio.sendString(B_button_IS_pressed)
// @highlight
        led.plot(4, 0)
    } else {
        radio.sendString(B_button_IS_NOT_pressed)
 // @highlight
        led.unplot(4, 0)
    }
})
```
## What happens when we you press A and B together?
Both the top left pixel and the top right pixel will light up

## Finally let's add plot & unplot to our rotation / pitch forever block
Drag final ``||basic:Basic:Forever||`` block onto your canvas to light up the reverse pixel
```blocks
basic.forever(function () {
    if (input.rotation(Rotation.Pitch) > 60) {
        led.plot(2, 4)
    } else {
        led.unplot(2, 4)
    }
})
```
<script src="https://makecode.com/gh-pages-embed.js"></script><script>makeCodeRender("{{ site.makecode.home_url }}", "{{ site.github.owner_name }}/{{ site.github.repository_name }}");</script>
