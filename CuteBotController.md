### @explicitHints true
# STEM - CuteBot Controller
## Step 1 - Let's build a micro:bit that can drive our CuteBot 
Let's build a micro:bit project that will drive a CuteBot by sending messages over radio signal. 
The A button will send "L" for left; the B button will send "R" for right; A+B together will send "F" for forwards.  
Tilting your micro:bit towards you will send "R" for reverse. Let's start by showing our micro:bit name.
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
To control our CuteBot we will need a Loop block; inside the loop block we will need and if statement
```blocks
loops.everyInterval(100, function () {
    if (true) {
    	
    }
})
```
## Step 4 - add number comparer
Drag in number comparer 
```blocks
loops.everyInterval(100, function () {
    if (0 == 0) {
    	
    }
})
```
## Step 5 - drag in pitch
Drag in pitch 
```blocks
loops.everyInterval(100, function () {
    if (input.rotation(Rotation.Pitch) == 60) {
    	
    }
})
```
## Step 6 - radio send "B" for Backwards
Drag in pitch 
```blocks
loops.everyInterval(100, function () {
    if (input.rotation(Rotation.Pitch) == 60) {
        radio.sendString("B")    	
    }
})
```
## Step 15 - download and test
Download your code onto your micro:bit to see it working

<script src="https://makecode.com/gh-pages-embed.js"></script><script>makeCodeRender("{{ site.makecode.home_url }}", "{{ site.github.owner_name }}/{{ site.github.repository_name }}");</script>

