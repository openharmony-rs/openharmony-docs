# Glossary

<!--Kit: Sensor Service Kit-->
<!--Subsystem: Sensors-->
<!--Owner: @dilligencer-->
<!--Designer: @andeszhang-->
<!--Tester: @zhaofangyuan-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=2cc3d788470dfc527ff67f0d956b9e3149129ee5 translatedAt=2026-08-20T06:25:09.110Z pushedAt=2026-08-20T13:23:34.462Z -->

## C

### continuous

One of the vibration event types in a custom vibration configuration file. It is capable of outputting strong, powerful vibration for a long duration, and you can configure the vibration curve through `Curve` to adjust the intensity and frequency.

## D

### Dynamic Vibrator

Multiple vibrators that are external to the device and support independent control. They can be flexibly managed based on information such as the device connection status and vibrator status, and are commonly used in external devices such as gamepads, remote controls, and external vibrators.

### Dynamic Sensor

An external sensor that supports dynamic connection. Its module capabilities allow fine-grained control of each dynamic sensor.

## L

### Local Vibrator

A vibrator built into the device, such as a rotor vibrator or linear vibrator.

### Local Sensor

A sensor built into the device, such as an accelerometer, gyroscope, or temperature sensor.

## P

### Preset Vibration

A vibration effect triggered by a built-in system `EffectId`, suitable for specific fixed scenarios. For example, the effect `haptic.clock.timer` is typically used to provide haptic feedback when a user adjusts a timer.

## T

### transient

One of the vibration event types in a custom vibration configuration file. The vibration is crisp and forceful, with a short duration.