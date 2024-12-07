# STEM - Code Club Badge
## Step 1 - Let's build a Code Club Badge 
Let's build a Code Club Badge to show your Code Club Team's name and your micro:bit's name.
Let's start by creating a Variable called "Team", your micro:bit will use this to show your team name. Make sure you enter your Team name in the "Team" variable.
```template
//
```
```blocks
let Team = ""
Team = "Zork"
```
## Step 2 - Show your Team Name
Let's show your team name when the A button is pressed.
```blocks
input.onButtonPressed(Button.A, function () {
    basic.showString(Team)
})
```
## Step 3 - Show your micro:bit Name
Let's show your micro:bit's name when we press the B button.
```blocks
input.onButtonPressed(Button.B, function () {
    basic.showString(control.deviceName())
})
```
## Step 4 - Try it out on your micro:bit
Download your code onto your micro:bit to see it working

