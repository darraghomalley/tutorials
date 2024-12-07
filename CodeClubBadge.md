### @explicitHints true
# STEM - Code Club Badge
## Step 1 - Let's build a Code Club Badge 
Let's build a Code Club Badge to show your Code Club Team's name and your micro:bit's name.
Let's start by clicking ``||variables:make a variable||``; name the variable "Team", your micro:bit will use this to show your team name. 
Drag ``||variables:set Team = 0||`` into the ``||basic:on start||`` block.
Replace the 0 with a ``||text:""||`` block and enter your Team name in the ``||variables:set Team = ""||`` block.
```template
//
```
```blocks
let Team = ""
Team = "Zork"
```
## Step 2 - Show your Team Name
Let's show your team name when the A button is pressed.
Drag an ``||input:Input:on button A pressed||`` block onto the canvas.
Drag a ``||basic:Basic:show string||`` block onto ``||input:button A pressed||`` block.
Drag ``||variables:Variables:show string||`` into your ``||basic:show string||`` block.
```blocks
input.onButtonPressed(Button.A, function () {
    basic.showString(Team)
})
```
## Step 3 - Show your micro:bit Name
Drag a ``||input:Input:on button A pressed||`` block onto the canvas. Change A to B.
Drag a ``||basic:Basic:show string||`` block onto your ``||input:button B pressed||`` block.
Drag ``||control:Control:device name||`` into your ``||basic:show string||`` block.
``` blocks
input.onButtonPressed(Button.B, function () {
    basic.showString(control.deviceName())
})
```
## Step 4 - Try it out on your micro:bit
Click ``|Download|`` to download your code onto your micro:bit to see it working

<script src="https://makecode.com/gh-pages-embed.js"></script><script>makeCodeRender("{{ site.makecode.home_url }}", "{{ site.github.owner_name }}/{{ site.github.repository_name }}");</script>
