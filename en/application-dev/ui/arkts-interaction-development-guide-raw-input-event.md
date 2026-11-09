# Input Devices and Events
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhou-chaobo-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=9c92183287fa23162e04874223c3b068eb1f8a4d translatedAt=2026-11-05T11:15:31.477Z pushedAt=2026-11-09T08:24:26.857Z nl=1 -->

Different input devices generate distinct types of basic events, which are triggered only when users interact with specific hardware or tools. These events can be categorized based on the source device and the tool used to initiate the interaction.

- Input device (source type): the type of device from which the event originates, i.e., the device that actually generates the low-level event, such as a touchscreen, mouse, keyboard, or joystick.
- Input tool (source tool): the specific tool used to generate the event. For example, to generate a touch event on a touchscreen, the tool used can be a finger or a stylus.

>  **NOTE** 
>
> It is recommended to use the gesture system directly for handling interactions, so you do not need to concern yourself with the differences between basic events.


[Touchscreen input events](./arkts-interaction-development-guide-touch-screen.md): covers touch interactions from touchscreen devices.

[Mouse input events](./arkts-interaction-development-guide-mouse.md): explains mouse-generated events and usage patterns.

[Touchpad input events](./arkts-interaction-development-guide-touchpad.md): explains touchpad-generated events and usage patterns.

[Keyboard input events](./arkts-interaction-development-guide-keyboard.md): explains keyboard-generated events and usage patterns.

[Gamepad input events](./arkts-interaction-development-guide-gamepad.md): explains gamepad-generated events and usage patterns.

[Crown input events](./arkts-common-events-crown-event.md): explains crown-generated events and usage patterns.
