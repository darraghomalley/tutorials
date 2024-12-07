### @explicitHints true
# STEM - Quick Draw
## Step 1 - Let's build a Quick Draw app 
Let's build a Quick Draw project that will send your micro:bit's name to your teacher.
Let's start by showing your micro:bit's name when it starts up.
```template
//
```
```blocks
basic.showString(control.deviceName());
})
```
## Step 2 - Set your radio group
Let's set your Radio Group; for this project the whole class will use radio group 255
```blocks
basic.showString(control.deviceName());
radio.setGroup(255)
})
```
## Step 3 - Set your radio group
Let's send your micro:bit's name using radio send string
```blocks
input.onButtonPressed(Button.A, function () {
    radio.sendString(control.deviceName())
})
```
## Step 4 - Try it out on your micro:bit
Download your code onto your micro:bit to see it working

