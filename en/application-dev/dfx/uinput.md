# uinput

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @Brilliantry_Rui-->

uinput can simulate operations on devices such as the mouse, keyboard, and touchpad for pressure tests like stability tests.

## Environment Setup

- The [environment setup](hdc.md#environment-setup) is complete.

- The devices are properly connected and **hdc shell** is executed.

## Features

**Usage**
```bash
uinput <option> <command> <arg> ...
```

**Available Commands**
| Abbreviation | Full Command  | Description       | 
| -------- | --------   | --------       |
| -M       | --mouse    | Injects a mouse event. | 
| -K       | --keyboard | Injects a keyboard event. |
| -S       | --stylus   | Injects a stylus event.| 
| -T       | --touch    | Injects a touch event. |
| -P       | --touchpad | Injects a touchpad event.|
| -?       | --help     | Displays the help information.     | 

> **NOTE**
>
> The unit of the coordinate-related parameters in the command is [px (pixel units)](../reference/apis-arkui/arkui-ts/ts-pixel-units.md).

## Help Command

Displays the commands supported by uinput.

**Command**
```bash
uinput -? 
uinput --help
```

**Example**
```bash
# Displays the help information.
uinput -? 

# Execution result.
Usage: uinput <option> <command> <arg>...
The options are:
-K  --keyboard
commands for keyboard:
-d <key>                   --down   <key>     -press down a key
-u <key>                   --up     <key>     -release a key
-l <key> [long press time] --long_press <key> [long press time] -press and hold the key
-r <key> [repeat output time] --repeat output <key> [repeat output time] -press and hold the key
-i <time>                  --interval <time>  -the program interval for the (time) milliseconds

...

```

## Mouse Events

Simulates mouse events, such as moving and clicking.

### Mouse Move Event
Simulates a mouse movement to the coordinates (dx, dy) in a relative coordinate system whose origin is the upper left corner of the specified screen.

**Command**
```bash
uinput -M -m <dx> <dy>
uinput --mouse --move <dx> <dy>

# <dx> <dy> Position coordinates in the relative coordinate system with the upper left corner of the screen as the origin.
```

**Example**
```bash
# Simulates a mouse movement to the coordinates (100, 100) in a relative coordinate system whose origin is the upper left corner of the specified screen.
uinput -M -m 100 100
```

**Extended Commands**
```bash
uinput -M -m <dx1> <dy1> <dx2> <dy2> [smooth time] --trace
uinput --mouse --move <dx1> <dy1> <dx2> <dy2> [smooth time] --trace

# <dx1> <dy1> Position coordinates of the mouse move start point in the relative coordinate system with the upper left corner of the screen as the origin.
# <dx2> <dy2> Position coordinates of the mouse move end point in the relative coordinate system with the upper left corner of the screen as the origin.
# The --trace option can be used to simulate the movement position and trace of the mouse to the coordinates in a relative coordinate system whose origin is the upper left corner of the specified screen.
# [smooth time]: movement time, in milliseconds. The default value is 1000. The value range is [1,15000]. Only an integer is supported.
```

**Example**
```bash
# Move a mouse pointer from (100, 100) to (200, 200) for 1500 ms.
uinput -M -m 100 100 200 200 1500 --trace
```

### Mouse Down Event
Simulates the pressing of the mouse button. It is recommended that this event be used together with the mouse button release event to ensure that the event is closed. buttonId: [Mouse Buttons](#mouse-buttons).

**Command**
```bash
uinput -M -d <buttonId>
uinput --mouse --down <buttonId>
```

### Mouse Up Event
Simulates the release of the mouse button. It is recommended that this event be used together with the mouse button press event to ensure that the event is closed. buttonId: [Mouse Buttons](#mouse-buttons).

**Command**
```bash
uinput -M -u <buttonId>
uinput --mouse --up <buttonId>
```

**Example**
```bash
# Simulates the pressing and releasing of the left mouse button.
uinput -M -d 0 -u 0
```

### Click Event
Simulates a mouse click. buttonId: [Mouse Buttons](#mouse-buttons).

**Command**
```bash
uinput -M -c <buttonId>
uinput --mouse --click <buttonId>
```

**Example**
```bash
# Simulates the clicking of the left mouse button.
uinput -M -c 0
```

### Double-Click Event
Simulates a double-click on the mouse button. buttonId: [Mouse Buttons](#mouse-buttons).

**Command**
```bash
uinput -M -b <dx> <dy> <buttonId> [press time] [click interval time]
uinput --mouse --double_click <dx> <dy> <buttonId> [press time] [click interval time]

# <dx> <dy>: position coordinates of the relative coordinate system with the upper left corner of the screen as the origin.
# [press time]: first pressing time, which is optional. The unit is ms. The default value is 50. The value range is [1,300]. Only an integer is supported.
# [click interval time]: click interval, which is optional. The unit is ms. The default value is 300. The value range is [1,450]. Only an integer is supported.
```

**Example**
```bash
# Simulates a left mouse button double-click at (100, 150).
uinput -M -b 100 150 0 10 10
```

### Mouse Scroll Event
Simulates the forward or backward scrolling of the mouse wheel. This command must be used together with the mouse movement event.

**Command**
```bash
uinput -M -m <dx1> <dy1> -s <number>
uinput --mouse --move <dx1> <dy1> --scroll <number>

# <dx1> <dy1>: position coordinates of the relative coordinate system with the upper left corner of the screen as the origin.
# <number>: number of mouse wheel scrolling scales. A positive number indicates backward scrolling, and a negative number indicates forward scrolling. One scale is 15. The value must be an integer.
```

**Example**
```bash
# Simulates the mouse moving to the position (100, 200) of the relative coordinate system with the upper left corner of the specified screen as the origin, and the mouse wheel scrolling backward by three scales.
uinput -M -m 100 200 -s 45
```

### Mouse Drag Event
Simulates a mouse dragging.

**Command**
```bash
uinput -M -g <dx1> <dy1> <dx2> <dy2> [total time]
uinput --mouse --drag <dx1> <dy1> <dx2> <dy2> [total time]

# <dx1> <dy1>: position coordinates of the mouse dragging start point of the relative coordinate system with the upper left corner of the screen as the origin.
# <dx2> <dy2>: position coordinates of the mouse dragging end point of the relative coordinate system with the upper left corner of the screen as the origin.
# [total time]: total dragging duration, in ms. This parameter is optional. The value is an integer ranging from 1 to 15000. The default value is 1000.
```

**Example**
```bash
# Simulates the left mouse button pressing, dragging from (200, 650) to (500, 300) in 15000 ms, and then releasing the left mouse button.
uinput -M -g 200 650 500 300 15000
```

### Mouse Event Interval
Sets the interval between mouse events, in ms. This command must be used together with other mouse event commands. Otherwise, this command is invalid.

**Command**
```bash
uinput -M -i <time>
uinput --mouse --interval <time>

# <time> Interval between mouse events, in milliseconds. The value is an integer ranging from 1 to 15000.
```

**Example**
```bash
# Simulate the left mouse button click at an interval of 500 ms.
uinput -M -c 0 -i 500 -c 0
```

### Mouse Buttons
| buttonId |  Description|
| -------- | -------- |
| 0  | Left mouse button.  |
| 1  | Right mouse button.  |
| 2  | Middle mouse button.  |
| 3  | Side mouse button.|
| 4  | Extended mouse button.|
| 5  | Mouse forward button.|
| 6  | Mouse back button.|
| 7  | Mouse task button.|

## Keyboard Events

Simulate keyboard input.

### Key Down Event
Simulate the pressing of a key on the keyboard. It is recommended that this event be used together with the keyboard key release event to ensure that the event is closed. keyCode: [Key value definition](../reference/apis-input-kit/js-apis-keycode.md).

**Command**
```bash
uinput -K -d <keyCode>
uinput --keyboard --down <keyCode>
```

### Key Up Event
Simulate the release of a key on the keyboard. This event must be used together with the keyboard key press event to ensure that the event is closed. keyCode: [Key value definition](../reference/apis-input-kit/js-apis-keycode.md).

**Command**
```bash
uinput -K -u <keyCode>
uinput --keyboard --up <keyCode>
```

**Example**
```bash
# Simulate the pressing and releasing of the A key.
uinput -K -d 2017 -u 2017
```

### Long-Press Key Event
Simulate the pressing and holding of a key on the keyboard for a specified period of time. You do not need to inject the keyboard key release event again. No key press event is injected during the long press. keyCode: [Key value definition](../reference/apis-input-kit/js-apis-keycode.md).

**Command**
```bash
uinput -K -l <keyCode> [long press time]
uinput --keyboard --long_press <keyCode> [long press time]

# [long press time] Long press time, in milliseconds. This parameter is optional. The default value is 3000. The value is an integer ranging from 3000 to 15000.
```

**Example**
```bash
# Simulates the scenario where the A key is pressed and held for 6000 ms and then released.
uinput -K -l 2017 6000
```

### Repeat Key Event
Simulates the scenario where a key is pressed and held for a specified period of time and then released. You do not need to inject the key release event again. Key press events are repeatedly injected during the long press. keyCode: [Key value definition](../reference/apis-input-kit/js-apis-keycode.md).

**Command**
```bash
uinput -K -r <keyCode> [repeat output time]
uinput --keyboard --repeat <keyCode> [repeat output time]

# [repeat output time]: duration for repeatedly reporting key press events, in ms. This parameter is optional. The default value is 3000. The value range is [3000,15000]. Only an integer is supported.
```

**Example**
```bash
# Simulates the scenario where the A key is pressed and repeatedly input within 4000 ms.
uinput -K -r 2017 4000
```

### Keyboard Event Interval
Sets the program interval of keyboard events, in ms. This command must be used together with other keyboard event commands. Otherwise, this command is invalid.

**Command**
```bash
uinput -K -i <time>
uinput --keyboard --interval <time>

# <time>: interval of keyboard events, in ms. The value range is [1,15000]. Only an integer is supported.
```

**Example**
```bash
# Simulates the scenario where the A key is pressed and released at an interval of 500 ms.
uinput -K -d 2017 -i 500 -u 2017
```

### Keyboard Text Event
Simulates text input using the keyboard. This command cannot be used together with other commands. Only a maximum of 2000 ASCII characters are supported.

**Command**
```bash
uinput -K -t <text>
uinput --keyboard --text <text>
```

**Example**
```bash
# Simulates the scenario where a piece of text "Hello,World!" is entered.
uinput -K -t Hello,World!
```

## Stylus Events

Simulates the scenario where a stylus is tapped or swiped. The actual injection effect is the same as that of the [touch event](#touch event). You are advised to use the touch event command first.

### Stylus Down Event
Simulates the action of pressing the stylus at (dx, dy). It is recommended that this command be used together with the stylus lift event to ensure that the event is closed.

**Command**
```bash
uinput -S -d <dx> <dy>
uinput --stylus --down <dx> <dy>

# <dx> <dy>: position coordinates of the relative coordinate system with the upper left corner of the screen as the origin.
```

### Stylus Up Event
Simulates the action of lifting the stylus at (dx, dy). It is recommended that this command be used together with the stylus press event to ensure that the event is closed.

**Command**
```bash
uinput -S -u <dx> <dy>
uinput --stylus --up <dx> <dy>

# <dx> <dy>: position coordinates of the relative coordinate system with the upper left corner of the screen as the origin.
```

**Example**
```bash
# Simulates the action of pressing and lifting the stylus at (100, 100).
uinput -S -d 100 100 -u 100 100
```

### Stylus Move Event
Simulates the action of pressing the stylus at (dx1, dy1), moving the stylus to (dx2, dy2) within a specified period of time, and lifting the stylus.

**Command**
```bash
uinput -S -m <dx1> <dy1> <dx2> <dy2> [smooth time] [-k keep time]
uinput --stylus --move <dx1> <dy1> <dx2> <dy2> [smooth time] [-k keep time]

# <dx1> <dy1>: position coordinates of the relative coordinate system with the upper left corner of the screen as the origin, where the stylus is pressed.
# <dx2> <dy2>: position coordinates of the relative coordinate system with the upper left corner of the screen as the origin, where the stylus is lifted.
# [smooth time]: movement time. This parameter is optional. The unit is ms. The default value is 1000. The value range is [1,15000]. Only an integer is supported.
# [-k keep time]: dwell time before the stylus is lifted after it is moved to the target position. This parameter is optional. The unit is ms. The default value is 0. The value range is [0,60000]. Only an integer is supported.
```

**Example**
```bash
# Simulates the action of pressing the stylus at (100, 1000), moving the stylus to (100, 2000) within 1000 ms, holding the stylus for 1000 ms, and lifting the stylus.
uinput -S -m 100 1000 100 2000 1000 -k 1000
```

### Stylus Click Event
Simulates a stylus click at (dx, dy).

**Command**
```bash
uinput -S -c <dx> <dy> [click interval]
uinput --stylus --click <dx> <dy> [click interval]

# <dx> <dy>: position coordinates of the relative coordinate system with the upper left corner of the screen as the origin.
# [click interval]: click interval, in milliseconds. The value is an integer ranging from 1 to 450. The default value is 100. This parameter is optional.
```

**Example**
```bash
# Simulate a touch pen click at the (100, 100) position.
uinput -S -c 100 100
```

### Stylus Drag Event
Simulates a touch pen drag.

**Command**
```bash
uinput -S -g <dx1> <dy1> <dx2> <dy2> [press time] [total time] 
uinput --stylus --drag <dx1> <dy1> <dx2> <dy2> [press time] [total time] 

# <dx1> <dy1>: position coordinates of the relative coordinate system with the upper left corner of the screen as the origin.
# <dx2> <dy2>: position coordinates of the relative coordinate system with the upper left corner of the screen as the origin.
# [press time]: press time, in milliseconds. This parameter is optional and must be used together with total time. If either of them is not specified, the command does not take effect. If both of them are not specified, the command takes effect. The value is an integer ranging from 500 to 14500. The default value is 500.
# [total time]: drag time, in milliseconds. This parameter is optional and must be used together with press time. If either of them is not specified, the command does not take effect. If both of them are not specified, the command takes effect. The value is an integer ranging from 1000 to 15000. The default value is 1000. [total time] - [press time] cannot be less than 500. Otherwise, the error message "total time input is error" is displayed.
```

**Example**
```bash
# Simulates a stylus touch and drag event. The stylus touches down at (100, 150) for 500 ms, drags to (500, 300) for 1100 ms, and then releases.
uinput -S -g 100 150 500 300 500 1100
```

### Interval of Stylus Events
Sets the interval between stylus touch events, in milliseconds. This command must be used together with other stylus touch event commands. Otherwise, this command is invalid.

**Command**
```bash
uinput -S -i <time>
uinput --stylus --interval <time>

# <time>: interval, in milliseconds. The value is an integer ranging from 1 to 15000.
```

**Example**
```bash
# Simulates a stylus touch event. The stylus touches down at (100, 100) and then lifts up at (100, 100) after 500 ms.
uinput -S -d 100 100 -i 500 -u 100 100
```

## Touch Events

Simulates a finger touch event, such as touch down and touch up.

### Touch Down Event
Simulates a finger touch down event at (dx, dy). It is recommended that this command be used together with the touch up event to ensure that the event is closed.

**Command**
```bash
uinput -T -d <dx> <dy>
uinput --touch --down <dx> <dy>

# <dx> <dy>: position coordinates of the relative coordinate system with the upper left corner of the screen as the origin.
```

### Touch Up Event
Simulates a finger touch up event at (dx, dy). It is recommended that this command be used together with the touch down event to ensure that the event is closed.

**Command**
```bash
uinput -T -u <dx> <dy>
uinput --touch --up <dx> <dy>

# <dx> <dy>: position coordinates of the relative coordinate system with the upper left corner of the screen as the origin.
```

**Example**
```bash
# Simulates a finger touch down and touch up event at (100, 100).
uinput -T -d 100 100 -u 100 100
```

### Touch Move Event
Simulates a finger touch move event. The finger touches down at (dx1, dy1), moves to (dx2, dy2) within a specified period, and then lifts up. A maximum of three fingers can move at the same time.

**Command**
```bash
uinput -T -m <dx1> <dy1> <dx2> <dy2> [-k keep time] [smooth time]
uinput --touch --move <dx1> <dy1> <dx2> <dy2> [-k keep time] [smooth time]

# <dx1> <dy1> Position coordinates of the touch start point in the relative coordinate system with the upper left corner of the screen as the origin.
# <dx2> <dy2> Position coordinates of the touch end point in the relative coordinate system with the upper left corner of the screen as the origin.
# [-k keep time] Touch hold time. This parameter is optional. The unit is ms. The default value is 0. The value range is [0,60000]. Only integers are supported.
# [smooth time] Touch move time. This parameter is optional. The unit is ms. The default value is 1000. The value range is [1,15000]. Only integers are supported.
```

**Example**
```bash
# Simulate a finger to touch and hold at (100, 1000), move to (100, 2000) in 1000 ms, hold for 1000 ms, and then lift.
uinput -T -m 100 1000 100 2000 -k 1000 1000

# Simulate three-finger swipe. The first finger touches and moves from (300, 900) to (300, 2000), the second finger touches and moves from (600, 900) to (600, 2000), and the third finger touches and moves from (900, 900) to (900, 2000). The total move duration is 200 ms. After the move is complete, the finger stays on the screen for 1000 ms and then lifts.
uinput -T -m 300 900 300 2000 600 900 600 2000 900 900 900 2000 -k 1000 200
```

### Touch Click Event
Simulates a finger click at coordinates (dx, dy).

**Command**
```bash
uinput -T -c <dx> <dy> [click interval]
uinput --touch --click <dx> <dy> [click interval]

# <dx> <dy> Position coordinates in the relative coordinate system with the upper left corner of the screen as the origin.
# [click interval] Click interval. This parameter is optional. The unit is ms. The default value is 100. The value range is [1,450]. Only integers are supported.
```

**Example**
```bash
# Simulate a finger to touch and click at (100, 100).
uinput -T -c 100 100
```

### Touch Drag Event
Simulate a finger to touch and drag.

**Command**
```bash
uinput -T -g <dx1> <dy1> <dx2> <dy2> [press time] [total time] 
uinput --touch --drag <dx1> <dy1> <dx2> <dy2> [press time] [total time] 

# <dx1> <dy1>: coordinates of the touch drag start point in the relative coordinate system with the upper left corner of the screen as the origin.
# <dx2> <dy2>: coordinates of the touch drag end point in the relative coordinate system with the upper left corner of the screen as the origin.
# [press time]: press time. This parameter is optional. It must be used together with total time. If either of them is not specified, the command does not take effect. If both of them are not specified, the command takes effect. The unit is ms. The default value is 500. The value range is [500,14500]. Only an integer is supported.
# [total time]: drag time. This parameter is optional. It must be used together with press time. If either of them is not specified, the command does not take effect. If both of them are not specified, the command takes effect. The unit is ms. The default value is 1000. The value range is [1000,15000]. Only an integer is supported. [total time] - [press time] cannot be less than 500. Otherwise, the error message "total time input is error" is displayed.
```

**Example**
```bash
# Touch at (100, 150), drag to (500, 300) over 1100 ms, then lift the finger.
uinput -T -g 100 150 500 300 500 1100
```

### Interval of Touch Events
Set the interval between touch events in ms. This command must be used together with other touch event commands. Otherwise, this command does not take effect.

**Command**
```bash
uinput -T -i <time>
uinput --touch --interval <time>

# <time>: interval, in ms. The value range is [1,15000]. Only an integer is supported.
```

**Example**
```bash
# Simulate a finger to press (100, 100), wait for 500 ms, and lift (100, 100).
uinput -T -d 100 100 -i 500 -u 100 100
```

### Single-Finger Double-Knuckle Tap
Simulates a single-finger double-knuckle tap on the touchscreen.

**Command**
```bash
uinput -T -k -s <dx1> <dy1> <dx2> <dy2> [interval time]
uinput --touch --knuckle --single <dx1> <dy1> <dx2> <dy2> [interval time]

# <dx1> <dy1> The first tap of a single knuckle in the relative coordinate system with the upper left corner of the screen as the origin.
# <dx2> <dy2> The second tap of a single knuckle in the relative coordinate system with the upper left corner of the screen as the origin.
# [interval time] Interval, in milliseconds. This parameter is optional. The default value is 200. The value range is [1,250]. Only integers are supported.
```

**Example**
```bash
# Simulate a single knuckle to tap at (100, 100) and (100, 130) at an interval of 200 ms.
uinput -T -k -s 100 100 100 130
```

### Two-Finger Double-Knuckle Tap
Simulates a two-finger double-knuckle tap on the touchscreen.

**Command**
```bash
uinput -T -k -d <dx1> <dy1> <dx2> <dy2> [interval time]
uinput --touch --knuckle --double <dx1> <dy1> <dx2> <dy2> [interval time]

# <dx1> <dy1> Position coordinates of the first knuckle in the relative coordinate system with the upper left corner of the screen as the origin.
# <dx2> <dy2> Position coordinates of the second knuckle in the relative coordinate system with the upper left corner of the screen as the origin.
# [interval time] Interval, in milliseconds. This parameter is optional. The default value is 200. The value range is [1,250]. Only integers are supported.
```

**Example**
```bash
# Simulate two knuckles to tap at (100, 100) and (100, 130) at an interval of 200 ms twice.
uinput -T -k -d 100 100 100 130
```

## Touchpad Events

### Touchpad Pinch Event
Simulates a finger pinch on the touchpad.

**Command**
```bash
uinput -P -p <dx> <dy> scalePercent
uinput --touchpad --pinch <dx> <dy> scalePercent

# <dx> <dy> Position coordinates of the relative coordinate system with the upper left corner of the screen as the origin.
# scalePercent Scale percentage. The value range is [1,500]. If the value is less than 100, the image is zoomed out. If the value is greater than 100, the image is zoomed in. The value of dx must be greater than 0, and the value of dy must be greater than or equal to 200. In this scenario, only image zooming is supported. Ensure that an image is on the desktop when this command is called.
```

**Example**
```bash
# Simulates a finger pinch on the touchpad.
uinput -P -p 100 300 89
```

### Touchpad Swipe Event
Simulates a swipe on the touchpad.

**Command**
```bash
uinput -P -s <startX> <startY> <endX> <endY>
uinput --touchpad --swipe <startX> <startY> <endX> <endY>

# <startX> <startY> Position coordinates of the start point of the swipe gesture reported by the touchpad in the relative coordinate system with the upper left corner of the screen as the origin.
# <endX> <endY> Position coordinates of the end point of the swipe gesture reported by the touchpad in the relative coordinate system with the upper left corner of the screen as the origin.
```

**Example**
```bash
# Simulate three-finger swipe gestures on the touchpad.
uinput -P -s 100 1100 100 300
```

### Touchpad Rotate Event
Simulates a rotation on the touchpad.

Currently, the touchpad rotation event does not take effect.

**Command**
```bash
uinput -P -r <rotateValue>
uinput --touchpad --rotate <rotateValue>

# <rotateValue> Rotation value, in degrees. The value range is [–359,359]. Only an integer is supported. A positive rotation angle indicates clockwise rotation, and a negative rotation angle indicates counterclockwise rotation.
```

**Example**
```bash
# Simulate two-finger rotation gestures (180°).
uinput -P -r 180
```
