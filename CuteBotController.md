### @explicitHints false

# STEM - CuteBot Controller

## Let's build a robot controller  @showdialog

Let's build a micro:bit project that will drive a CuteBot by sending messages over radio signal.

To help you out, we've created some variables that you will need later: ``||variables: Forwards, Backwards, Left, Right, Stop||``.

```validation.global

# BlocksExistValidator

```

```template

let Forwards = "FORWARDS"

let Backwards = "BACKWARDS"

let Left = "LEFT"

let Right = "RIGHT"

let Stop = "STOP"

let Direction = "STOP"

let Rainbow = "RAINBOW"

```

```blocks

let Forwards = "FORWARDS"

let Backwards = "BACKWARDS"

let Left = "LEFT"

let Right = "RIGHT"

let Stop = "STOP"

let Direction = "STOP"

let Rainbow = "RAINBOW"

```

## Show your micro:bit name

Let's start by dragging a ``||basic:Basic:show string||`` block into the top of ``||basic:on start||``.

Drag ``||control:Control:device name||`` into to ``||basic:show string||``; this will show your micro:bit's name.

 

```blocks

// @highlight

basic.showString(control.deviceName())

let Forwards = "FORWARDS"

let Backwards = "BACKWARDS"

let Left = "LEFT"

let Right = "RIGHT"

let Stop = "STOP"

let Direction = "STOP"

let Rainbow = "RAINBOW"

```

## Set your radio group

Drag a ``||radio:Radio:set group||`` block into ``||basic:on start||``; enter your radio group number. Use a ``||basic:Basic:show string||`` block to show your radio group number.

```blocks

basic.showString(control.deviceName())

//@highlight

radio.setGroup(1)

//@highlight

basic.showString("1")

let Forwards = "FORWARDS"

let Backwards = "BACKWARDS"

let Left = "LEFT"

let Right = "RIGHT"

let Stop = "STOP"

let Direction = "STOP"

let Rainbow = "RAINBOW"

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

let Direction = Stop

})

```

## Check for button A (left)

Drag an ``||logic:if true then||`` block into the ``||loops:every 100ms||`` block.

Drag a ``||input:button A is pressed||`` block into the ``||logic:if true then||`` block. Drag a ``||variables:set Direction = 0||`` block inside the ``||logic:if||`` statement. Replace the 0 with ``||variables:Left||``.

```blocks

loops.everyInterval(100, function () {

let Direction = Stop

    // @highlight

    if (input.buttonIsPressed(Button.A)) {

        Direction = Left

    }

})

```

## Check for button B (right)

Duplicate the ``||logic:if button A is pressed||`` block (right click, then duplicate) and drag it underneath the ``||logic:if button A is pressed||`` block; change the button to B and the direction to ``||variables:Right||``.

```blocks

loops.everyInterval(100, function () {

let Direction = Stop

    if (input.buttonIsPressed(Button.A)) {

        Direction = Left

    }

    // @highlight

    if (input.buttonIsPressed(Button.B)) {

        Direction = Right

    }

})

```

## Check for button A+B (forwards)

Duplicate the ``||logic:if button B is pressed||`` block (right click, then duplicate) and drag it underneath the ``||logic:if button B is pressed||`` block; change the button to A+B and the direction to ``||variables:Forwards||``.

```blocks

loops.everyInterval(100, function () {

let Direction = Stop

    if (input.buttonIsPressed(Button.A)) {

        Direction = Left

    }

    if (input.buttonIsPressed(Button.B)) {

        Direction = Right

    }

    // @highlight

    if (input.buttonIsPressed(Button.AB)) {

        Direction = Forwards

    }

})

```

## Check for tilt backwards (Backwards)

Drag an ``||logic:if true then||`` block into the bottom of the ``||loops:every 100ms||`` block.

Drag a ``||logic:Logic:0>0||`` comparision block into the ``||logic:if||`` block.

Drag ``||input:Input:rotation||`` into left side of the number comparision and set to ">" 60 (greater than 60).

Drag ``||variables:Variables: set xyz = 0||`` inside the ``||logic:if||`` block and set ``||variables:Direction||`` to ``||variables:Backwards||``.

```blocks

loops.everyInterval(100, function () {

let Direction = Stop

    if (input.buttonIsPressed(Button.A)) {

        Direction = Left

    }

    if (input.buttonIsPressed(Button.B)) {

        Direction = Right

    }

   

    if (input.buttonIsPressed(Button.AB)) {

        Direction = Forwards

    }

    // @highlight

    if (input.rotation(Rotation.Pitch) > 60) {

        Direction = Backwards

    }

})

```

## Finally, let's send our command to the Cutebot

Drag ``||radio:Radio:send string||`` into the bottom of the the ``||loops:loops.everyInterval(100)||`` block.

Set the message to ``||variables:Direction||``; this will send a direction command to the CuteBot.

```blocks

loops.everyInterval(100, function () {

let Direction = Stop

    if (input.buttonIsPressed(Button.A)) {

        Direction = Left

    }

    if (input.buttonIsPressed(Button.B)) {

        Direction = Right

    }

   

    if (input.buttonIsPressed(Button.AB)) {

        Direction = Forwards

    }

    if (input.rotation(Rotation.Pitch) > 60) {

        Direction = Backwards

    }

    // @highlight

    radio.sendString(Direction)

})

```

## 100ms Frequency @showdialog

Your micro:bit will send a Direction message to your CuteBot every 100 milliseconds, that's 10 times a second. Wow, that's really fast, try saying forwards 10 times in 1 second.

 

## Let's also send a "Rainbow" lights command to the CuteBot by using on logo pressed

To flash the Cutebot's lights, drag a ``||input:Input:on logo pressed||`` block onto canvas and use ``||radio:Radio:send string||`` to send the variable ``||variables:Rainbow||``

```blocks

// @highlight

input.onLogoEvent(TouchButtonEvent.Pressed, function () {

    radio.sendString(Rainbow)

})

```

## Download and test - good luck and happy racing!!!

Click ``|Download|`` to download your code onto your micro:bit to see it working. Good luck and happy racing!

 

<script src=https://makecode.com/gh-pages-embed.js></script><script>makeCodeRender("{{ site.makecode.home_url }}", "{{ site.github.owner_name }}/{{ site.github.repository_name }}");</script>