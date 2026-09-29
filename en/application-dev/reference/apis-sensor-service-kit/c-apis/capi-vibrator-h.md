# vibrator.h

## Overview

Declares the APIs for starting or stopping vibration. Two vibration modes are supported: simple continuous vibration and custom vibration sequence. Simple continuous vibration is suitable for scenarios that require a single vibration of a fixed duration, such as alarm clocks and timing reminders. You only need to specify the vibration duration. Custom vibration sequences are suitable for scenarios that require complex vibration patterns, such as notification reminders and game feedback. You can define a vibration sequence file to achieve rich tactile effects. This helps you implement precise vibration control and improve user interaction experience.

**Library**: libohvibrator.z.so

**Since**: 11

**Related module**: [Vibrator](capi-vibrator.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [int32_t OH_Vibrator_PlayVibration(int32_t duration, Vibrator_Attribute attribute)](#oh_vibrator_playvibration) | Configures the vibrator to vibrate continuously for a given duration. After the API is successfully called, the vibrator starts to vibrate immediately and automatically stops after the specified duration. This method is applicable to scenarios where the vibrator needs to vibrate for a fixed duration, such as alarm clock, timing reminder, game feedback, and message notification. |
| [int32_t OH_Vibrator_PlayVibrationCustom(Vibrator_FileDescription fileDescription, Vibrator_Attribute vibrateAttribute)](#oh_vibrator_playvibrationcustom) | Configures the vibrator to vibrate with the custom sequence. After the API is successfully called, the system plays the vibration effect based on the custom vibration sequence. This method is applicable to scenarios that require complex vibration patterns, such as notification reminders, games, and tactile feedback, to provide personalized vibration experiences and enhance user immersion. |
| [int32_t OH_Vibrator_Cancel()](#oh_vibrator_cancel) | Stops the vibration. After the API is successfully called, the ongoing vibration or custom vibration sequence is stopped immediately. This method is applicable to scenarios where vibration needs to be stopped immediately, such as when a user cancels an operation, switches between apps, or clears a system notification. It helps optimize user experience and reduce device power consumption. |

## Function description

### OH_Vibrator_PlayVibration()

```c
int32_t OH_Vibrator_PlayVibration(int32_t duration, Vibrator_Attribute attribute)
```

**Description**

Configures the vibrator to vibrate continuously for a given duration. After the API is successfully called, the vibrator starts to vibrate immediately and automatically stops after the specified duration. This method is applicable to scenarios where the vibrator needs to vibrate for a fixed duration, such as alarm clock, timing reminder, game feedback, and message notification.

**Required permission**: ohos.permission.VIBRATE

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t duration | Vibration duration, in milliseconds. It is used to control the duration of vibration. The value range is [1, 60000]. |
| [Vibrator_Attribute](capi-vibrator-vibrator-attribute.md) attribute | Vibration attribute, which is used to configure the vibration strength and mode. For details, see [Vibrator_Attribute](capi-vibrator-vibrator-attribute.md). |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | If the operation is successful, **0** is returned. Otherwise, an error code in [Vibrator_ErrorCode](capi-vibrator-type-h.md#vibrator_errorcode) is returned. Common error codes include: <br>**201**: **PERMISSION_DENIED** (The permission verification failed); <br>**401**: **PARAMETER_ERROR** (The parameter check fails); <br>**801**: **UNSUPPORTED** (It is not supported on the device). |

**Reference**:

[OH_Vibrator_Cancel](capi-vibrator-h.md#oh_vibrator_cancel) Stops the ongoing vibration
[OH_Vibrator_PlayVibrationCustom](capi-vibrator-h.md#oh_vibrator_playvibrationcustom) Configures the vibrator to vibrate with the custom sequence


### OH_Vibrator_PlayVibrationCustom()

```c
int32_t OH_Vibrator_PlayVibrationCustom(Vibrator_FileDescription fileDescription, Vibrator_Attribute vibrateAttribute)
```

**Description**

Configures the vibrator to vibrate with the custom sequence. After the API is successfully called, the system plays the vibration effect based on the custom vibration sequence. This method is applicable to scenarios that require complex vibration patterns, such as notification reminders, games, and tactile feedback, to provide personalized vibration experiences and enhance user immersion.

**Required permission**: ohos.permission.VIBRATE

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Vibrator_FileDescription](capi-vibrator-vibrator-filedescription.md) fileDescription | File descriptor of the custom vibration effect, which specifies the location and range of the file that contains the vibration sequence data. You can play a custom vibration effect by setting the file handle, offset address, and length. For details, see [Vibrator_FileDescription](capi-vibrator-vibrator-filedescription.md). |
| [Vibrator_Attribute](capi-vibrator-vibrator-attribute.md) vibrateAttribute | Vibration attribute, which is used to control the strength and frequency of the custom vibration effect. For details, see [Vibrator_Attribute](capi-vibrator-vibrator-attribute.md). |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | If the operation is successful, **0** is returned. <br>Otherwise, an error code in [Vibrator_ErrorCode](capi-vibrator-type-h.md#vibrator_errorcode) is returned. <br>If the parameters are incorrect, check whether the values of **fileDescription** and ** vibrateAttribute** are valid. If the device does not support vibration, check the device capability. For details about the error codes, see [Vibrator_ErrorCode](capi-vibrator-type-h.md#vibrator_errorcode). |

**Reference**:

[OH_Vibrator_Cancel](capi-vibrator-h.md#oh_vibrator_cancel) Stops the ongoing vibration


### OH_Vibrator_Cancel()

```c
int32_t OH_Vibrator_Cancel()
```

**Description**

Stops the vibration. After the API is successfully called, the ongoing vibration or custom vibration sequence is stopped immediately. This method is applicable to scenarios where vibration needs to be stopped immediately, such as when a user cancels an operation, switches between apps, or clears a system notification. It helps optimize user experience and reduce device power consumption.

**Required permission**: ohos.permission.VIBRATE

**Since**: 11

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | If the operation is successful, **0** is returned. Otherwise, an error code in [Vibrator_ErrorCode](capi-vibrator-type-h.md#vibrator_errorcode) is returned. For details about the possible causes and solutions, see the table below. |


