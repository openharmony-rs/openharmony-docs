# Vibrator

## Overview

Provides the enums, structs, and error codes used in the vibrator APIs.

**System capability**: SystemCapability.Sensors.MiscDevice

**Since**: 11

## Files

| Name | Description |
| -- | -- |
| [vibrator_type.h](capi-vibrator-type-h.md) | Declares the APIs for controlling vibration. This module supports multiple vibration scenarios, such as alarms, ringtones, notifications, communication, touch, media, physical feedback, and simulated reality. By setting vibration priorities, you can meet vibration requirements in different scenarios, improving user interaction experience and device usability. |
| [vibrator.h](capi-vibrator-h.md) | Declares the APIs for starting or stopping vibration. Two vibration modes are supported: simple continuous vibration and custom vibration sequence. Simple continuous vibration is suitable for scenarios that require a single vibration of a fixed duration, such as alarm clocks and timing reminders. You only need to specify the vibration duration. Custom vibration sequences are suitable for scenarios that require complex vibration patterns, such as notification reminders and game feedback. You can define a vibration sequence file to achieve rich tactile effects. This helps you implement precise vibration control and improve user interaction experience. |
