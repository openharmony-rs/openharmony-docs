# Glossary
<!--Kit: Sensor Service Kit-->
<!--Subsystem: Sensors-->
<!--Owner: @dilligencer-->
<!--Designer: @LiuChao-->
<!--Tester: @zhaofangyuan-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=2d7b4266499e3556fe42ddb8c4180af3db492816 translatedAt=2026-09-14T08:50:38.619Z pushedAt=2026-09-15T10:37:15.416Z -->

## C

### continuous

One of the vibration event types in a custom vibration configuration file. It is capable of outputting strong, powerful vibration for a long duration, and you can configure the vibration curve through `Curve` to adjust the intensity and frequency.

## D

### Dynamic Motor

Multiple motors that are external to the device and support independent control. They can be flexibly managed based on information such as the device connection status and motor status, and are commonly used in external devices such as gamepads, remote controls, and external vibrators.

### Dynamic Sensor

An external sensor that supports dynamic connection. Its module capabilities allow fine-grained control of each dynamic sensor.

## L

### Local Motor

A motor built into the device, such as a rotor motor or linear motor.

### Local Sensor

A sensor built into the device, such as an accelerometer, gyroscope, or temperature sensor.

## P

### Preset Vibration

A vibration effect triggered by a built-in system `EffectId`, suitable for specific fixed scenarios. For example, the effect `haptic.clock.timer` is typically used to provide haptic feedback when a user adjusts a timer.

## T

### transient

One of the vibration event types in a custom vibration profile. The vibration is crisp and forceful, with a short duration.
