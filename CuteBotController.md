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
## Add a Forever block to your canvas for button A
To control your CuteBot, drag a ``||basic:Basic:Forever||`` block onto your canvas
```blocks
// @highlight
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        radio.sendString("A is pressed")
        led.plot(0, 0)
    } else {
        radio.sendString("A is not pressed")
        led.unplot(0, 0)
    }
})
```
## Add a Forever block to your canvas for button B
Drag another ``||basic:Basic:Forever||`` block onto your canvas
```blocks
basic.forever(function () {
    if (input.buttonIsPressed(Button.B)) {
        radio.sendString("B is pressed")
        led.plot(4, 0)
    } else {
        radio.sendString("B is not pressed")
        led.unplot(4, 0)
    }
})
```
## Add a Forever block to check if you want to reverse
Drag another ``||basic:Basic:Forever||`` block onto your canvas for tilt backwards to reverse
```blocks
basic.forever(function () {
// @highlight
    radio.sendValue("Pitch", input.rotation(Rotation.Pitch))
})
```
## Use a final forever block to highlight a pixel for reverse
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
## Add radio send string "Rainbow" to on logo pressed 
To flash the Cutebot's lights, drag a ``||input:Input:on logo pressed||`` block onto canvas and use ``||radio:Radio:send string||`` to send "Rainbow" 
```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    radio.sendString("RAINBOW")
    basic.showString("RAINBOW")
})
```
## download and test
Click ``|Download|`` to download your code onto your micro:bit to see it working

<script src="https://makecode.com/gh-pages-embed.js"></script><script>makeCodeRender("{{ site.makecode.home_url }}", "{{ site.github.owner_name }}/{{ site.github.repository_name }}");</script>
