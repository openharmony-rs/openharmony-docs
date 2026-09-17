# vibrator.h

## Overview

Declares the APIs for starting or stopping vibration.

**Library**: libohvibrator.z.so

**System capability**: SystemCapability.Sensors.MiscDevice

**Since**: 11

**Related module**: [Vibrator](capi-vibrator.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [int32_t OH_Vibrator_PlayVibration(int32_t duration, Vibrator_Attribute attribute)](#oh_vibrator_playvibration) | Controls the vibrator to vibrate continuously for a given duration. |
| [int32_t OH_Vibrator_PlayVibrationCustom(Vibrator_FileDescription fileDescription, Vibrator_Attribute vibrateAttribute)](#oh_vibrator_playvibrationcustom) | Configure the vibrator to vibrate with the custom sequence. |
| [int32_t OH_Vibrator_Cancel()](#oh_vibrator_cancel) | Stops the vibration. |

## Function description

### OH_Vibrator_PlayVibration()

```c
int32_t OH_Vibrator_PlayVibration(int32_t duration, Vibrator_Attribute attribute)
```

**Description**

Controls the vibrator to vibrate continuously for a given duration.

**Required permission**: ohos.permission.VIBRATE

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t duration | Vibration duration, in milliseconds. |
| Vibrator_Attribute attribute | Vibration attribute. For details, see **VibrateAttribute**. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns 0 if the operation is successful; returns a non-zero value otherwise.  For details, see {@link Vibrator_ErrorCode}. |

### OH_Vibrator_PlayVibrationCustom()

```c
int32_t OH_Vibrator_PlayVibrationCustom(Vibrator_FileDescription fileDescription, Vibrator_Attribute vibrateAttribute)
```

**Description**

Configure the vibrator to vibrate with the custom sequence.

**Required permission**: ohos.permission.VIBRATE

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| Vibrator_FileDescription fileDescription | File descriptor of the custom vibration effect. For details, see {@link Vibrator_FileDescription}. |
| Vibrator_Attribute vibrateAttribute | Vibration attribute. For details, see {@link Vibrator_Attribute}. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns 0 if the operation is successful; returns a non-zero value otherwise.  For details, see {@link Vibrator_ErrorCode}. |

### OH_Vibrator_Cancel()

```c
int32_t OH_Vibrator_Cancel()
```

**Description**

Stops the vibration.

**Required permission**: ohos.permission.VIBRATE

**Since**: 11

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns 0 if the operation is successful; returns a non-zero value otherwise.  For details, see {@link Vibrator_ErrorCode}. |


