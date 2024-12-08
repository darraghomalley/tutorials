### @explicitHints true
# STEM - Quick Draw
## Step 1 - Let's build a Quick Draw app 
Let's build a Quick Draw project that will send your micro:bit's name to your teacher.
Let's start by showing your micro:bit's name when it starts up.
Drag a ``||basic:Basic:show string||`` block into ``||basic:on start||``
Drag ``||control:device name||`` into ``||basic:show string||``

```template
//
```
```blocks
basic.showString(control.deviceName());
})
```
## Step 2 - Set your radio group
Let's set your Radio Group; for this project the whole class will use radio group 255. Drag ``||radio:Radio:set radio group = 0||`` into ``||basic:on start||``.
Set the radio group to 255.
```blocks
basic.showString(control.deviceName());
radio.setGroup(255)
})
```
## Step 3 - Send your micro:bit's name over radio using A+B 
Drag ``||input:Input:on button A pressed||`` onto your canvas; change A to A+B.
Drag ``||radio:Radio:send string||`` into ``||input:on button A pressed||`` 
Drag ``||control:Control:device name||`` into ``||radio:send string||`` 
```blocks
input.onButtonPressed(Button.AB, function () {
    radio.sendString(control.deviceName())
})
```
## Step 4 - Try it out on your micro:bit
Click ``|Download|`` to download your code onto your micro:bit to see it working

<script src="https://makecode.com/gh-pages-embed.js"></script><script>makeCodeRender("{{ site.makecode.home_url }}", "{{ site.github.owner_name }}/{{ site.github.repository_name }}");</script>


