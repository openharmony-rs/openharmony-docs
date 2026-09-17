# Glossary

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=2b0645745065de6b5830e36c0926c45e4c14235d translatedAt=2026-09-01T02:17:49.688Z pushedAt=2026-09-01T12:39:39.290Z -->

## A

### Air Mouse Mode

An air operation mode of the stylus: Allows users to control the movement of a virtual cursor on the screen by moving the stylus in the air and use the stylus buttons to navigate up or down between pages. This mode is suitable for scenarios such as giving presentations and performing air interactions. After this mode is activated, the system automatically uses the hover cursor (`LASER_CURSOR`), click cursor (`LASER_CURSOR_DOT`), or laser pointer cursor (`LASER_CURSOR_DOT_RED`). Apps cannot directly set these cursor styles through the standard cursor style APIs. This mode differs from regular touch input, where the stylus writes on the screen.

## D

### Display Coordinate System

A relative coordinate system whose origin is the upper-left corner of a specified screen, measured in pixels, used to represent the position of input events such as mouse, touchscreen, and axis events on the screen. It differs from the global coordinate system, whose origin is the upper-left corner of the primary screen and whose coordinates are unified across screens; in multi-screen scenarios, the coordinate values of the two systems differ.

## E

### Event Injection

The capability to programmatically construct input events, such as key, mouse, touch, and axis events, and inject them into the system input channel to simulate real user input. This capability is mainly used in scenarios such as automated testing. Event injection must comply with event state constraints. For example, a key must be pressed before it is released, an axis event sequence must start before it is updated and then end, and the same touch point cannot be pressed repeatedly. Event injection is also subject to permission control: `ohos.permission.INJECT_INPUT_EVENT` is required for system-side use, while `ohos.permission.CONTROL_DEVICE` or prior user authorization for event injection is required for open capability use. Events generated through injection are marked as injected events.

### Event Interception

A mechanism by which an application intercepts and handles input events before the system dispatches them. It supports key, mouse, touchscreen, and axis events. Key event interception takes effect only when the application has focus, while mouse, touchscreen, and axis event interception takes effect only when the event hits the application window. If the same application adds interception repeatedly, only the first addition takes effect. This differs from event listening, which only observes events without blocking them.

### Event Redispatch

A mechanism that returns events intercepted by a key event hook to the system dispatch chain in their original priority order. It must be initiated within 3 seconds after interception, and the press and release (or cancel) events must remain paired. It is used when the hook does not consume the key after processing, allowing the event to continue normal dispatch.

## F

### Final Key

A key in a keyboard shortcut that is not a modifier key and determines the meaning of the key combination. Only one final key is allowed in a shortcut. For example, `A` is the final key in `Ctrl+Alt+A`. It is referred to as the final key in system APIs. Together with the set of modifier keys, the final key uniquely identifies a keyboard shortcut. When subscribing to a keyboard shortcut, the callback is triggered when the final key is pressed or released, depending on the subscription parameters.

### Fingerprint Gesture

Gesture events recognized and reported by the side-mounted fingerprint sensor, including press, lift, swipe, second press, and double tap. The events carry offsets relative to the long and short axes of the fingerprint sensor. This extends the fingerprint sensor from an identity authentication component to a touch input channel, distinguishing it from fingerprint recognition used for identity authentication.

## G

### Gesture Event

A high-level semantic event reported by the system after it completes recognition of underlying touch or touchpad data. It directly provides gesture results such as pinch, rotation, and multi-finger swipe, and is reported in an event sequence of start, update, and end (or cancel). Applications can respond to gestures without computing the raw touch point trajectory themselves, which distinguishes it from raw touch events.

### Global Coordinate System

A coordinate system that uses the upper left corner of the primary screen as the origin and takes values uniformly across multiple screens, measured in pixels. In a multi-screen scenario within a single screen group, coordinates are globally unique, and the global coordinates (`globalX`/`globalY`) of mouse events are expressed based on this coordinate system. Event injection based on global coordinates is used for precise cross-screen positioning, as opposed to the display coordinate system, which uses the upper left corner of a specified screen as the origin.

### Global Shortcut

A key or key combination that takes effect when pressed on any screen of the system, also known as a hotkey. It does not depend on a specific focused window and is managed and dispatched uniformly by the system. After subscribing through the global shortcut API, an application can respond to it even when it is not in the foreground. By definer, global shortcuts are classified into system shortcuts and application shortcuts. Before subscribing, avoid key combinations already occupied by the system or other applications. In special scenarios (such as factory mode), all system shortcuts can be disabled as a whole.

## H

### Hover Scroll

The behavior of scrolling the wheel while the mouse is hovering (without pressing any button) to scroll the content of the window beneath the hover position. It can be enabled or disabled through a system switch and is enabled by default. It controls whether wheel scrolling takes effect immediately upon hovering.
