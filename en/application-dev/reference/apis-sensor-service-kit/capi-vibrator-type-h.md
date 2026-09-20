# vibrator_type.h
<!--Kit: Sensor Service Kit-->
<!--Subsystem: Sensors-->
<!--Owner: @dilligencer-->
<!--Designer: @andeszhang-->
<!--Tester: @zhaofangyuan-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=2cc3d788470dfc527ff67f0d956b9e3149129ee5 translatedAt=2026-09-02T07:33:07.211Z pushedAt=2026-09-05T12:05:06.002Z -->

## Overview

Declares the APIs for controlling vibration. This module supports multiple vibration scenarios, such as alarms, ringtones, notifications, communication, touch, media, physical feedback, and simulated reality. By setting vibration priorities, you can meet vibration requirements in different scenarios, improving user interaction experience and device usability.

**Reference file**: <sensors/vibrator_type.h>

**Library**: libohvibrator.z.so

**System capability**: SystemCapability.Sensors.MiscDevice

**Since**: 11

**Related module**: [Vibrator](capi-vibrator.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [Vibrator_Attribute](capi-vibrator-vibrator-attribute.md) | Vibrator_Attribute | Vibrator attributes. For details, see [Vibrator_Attribute](capi-vibrator-vibrator-attribute.md). |
| [Vibrator_FileDescription](capi-vibrator-vibrator-filedescription.md) | Vibrator_FileDescription | Vibrator file description. For details, see [Vibrator_FileDescription](capi-vibrator-vibrator-filedescription.md). |

### Enumeration

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [Vibrator_ErrorCode](#vibrator_errorcode) | Vibrator_ErrorCode | Enumerates the error codes. |
| [Vibrator_Usage](#vibrator_usage) | Vibrator_Usage | Enumerates the vibration priorities in different scenarios. A vibration with a higher priority interrupts a vibration with a lower priority. You are advised to select a proper priority based on the application scenario. |

## Enum Description

### Vibrator_ErrorCode

```c
enum Vibrator_ErrorCode
```

**Description**

Enumerates the error codes. If an exception occurs during use of vibration APIs, the corresponding error code is returned.

**Since**: 11

| Enum Item| Description|
| -- | -- |
| PERMISSION_DENIED = 201 | Permission verification failed. Check whether you have requested the required permission (for example, **ohos.permission.VIBRATE**). |
| PARAMETER_ERROR = 401 | Parameter check failed. For example, a mandatory parameter is not passed in, or the parameter type passed in is incorrect. |
| UNSUPPORTED = 801 | The device does not support the API. This error code is reported when the device supports the SysCap but does not support a specific API. |
| DEVICE_OPERATION_FAILED = 14600101 | Device operation failed. Check the device status and parameter configuration. |

### Vibrator_Usage

```c
enum Vibrator_Usage
```

**Description**

Enumerates the vibration priorities in different scenarios. A vibration with a higher priority interrupts a vibration with a lower priority. Suggestions: Select a proper priority based on the application scenario. In scenarios where continuous vibration is required, keep the priority consistent to avoid performance loss caused by frequently switching priorities. It is recommended that a higher priority be used for physical feedback and touch vibrations to ensure timely response.

**Since**: 11

| Enum Item| Description|
| -- | -- |
| VIBRATOR_USAGE_UNKNOWN = 0 | Unknown scenario, with the lowest priority. Choose this option when the specific application scenario cannot be determined. In this case, the system complies with the default policy. |
| VIBRATOR_USAGE_ALARM = 1 | Alarm. Choose this option in scenarios such as alarm clock and countdown reminders. The vibration is strong and lasts for a long time. |
| VIBRATOR_USAGE_RING = 2 | Ringtone. Choose this option for incoming calls. The vibration mode is cyclic vibration, which helps users answer calls in a timely manner. |
| VIBRATOR_USAGE_NOTIFICATION = 3 | Notification. Choose this option in scenarios such as system notifications and app messages. The vibration is short, prompting users to view the notifications. |
| VIBRATOR_USAGE_COMMUNICATION = 4 | Communication. Choose this option in communication scenarios such as calls, instant messaging, and SMS messages. The vibration mode is one-shot vibration. |
| VIBRATOR_USAGE_TOUCH = 5 | Touch. Choose this option in feedback scenarios such as screen touches and key operations. The vibration is extremely short, providing a sense of operation confirmation. |
| VIBRATOR_USAGE_MEDIA = 6 | Media. Choose this option in media app scenarios such as music and videos. The vibration is synchronized with the media content to enhance the immersive experience. |
| VIBRATOR_USAGE_PHYSICAL_FEEDBACK = 7 | Physical feedback. Choose this option in scenarios that require physical feedback, such as games and simulations. It provides physical interaction experiences such as physical key feedback and tactile force feedback. The vibration mode can be customized to simulate real touch sensations. |
| VIBRATOR_USAGE_SIMULATED_REALITY = 8 | Simulated reality. Choose this option for tactile feedback in immersive scenarios such as VR/AR. The vibration intensity and mode are precisely controllable to provide realistic environmental feedback. |


