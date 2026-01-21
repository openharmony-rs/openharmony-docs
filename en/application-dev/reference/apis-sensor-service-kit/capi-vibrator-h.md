# vibrator.h
<!--Kit: Sensor Service Kit-->
<!--Subsystem: Sensors-->
<!--Owner: @dilligencer-->
<!--Designer: @butterls-->
<!--Tester: @murphy84-->
<!--Adviser: @hu-zhiqiong-->

## Overview

Declares the APIs for starting or stopping vibration.

**Header file**: <sensors/vibrator.h>

**Library**: libohvibrator.z.so

**System capability**: SystemCapability.Sensors.MiscDevice

**Since**: 11

**Related module**: [Vibrator](capi-vibrator.md)

## Summary

### Functions

| Name   | Description|
|------| -- |
| [int32_t OH_Vibrator_PlayVibration(int32_t duration, Vibrator_Attribute attribute)](#oh_vibrator_playvibration)                                        | Configures the vibrator to vibrate continuously for a given duration.|
| [int32_t OH_Vibrator_PlayVibrationCustom(Vibrator_FileDescription fileDescription, Vibrator_Attribute vibrateAttribute)](#oh_vibrator_playvibrationcustom) | Configures the vibrator to vibrate with the custom sequence.|
| [int32_t OH_Vibrator_Cancel()](#oh_vibrator_cancel)                    | Stops the vibration.|

## Function Description

### OH_Vibrator_PlayVibration()

```c
int32_t OH_Vibrator_PlayVibration(int32_t duration, Vibrator_Attribute attribute)
```

**Description**

Controls the vibrator to vibrate continuously for a given duration.

**Required permissions**: ohos.permission.VIBRATE

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| int32_t duration | Vibration duration, in milliseconds.|
| [Vibrator_Attribute](capi-vibrator-vibrator-attribute.md) attribute | Vibration attribute. For details, see **VibrateAttribute**.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns **0** if the operation is successful; returns a non-zero value otherwise. For details, see [Vibrator_ErrorCode](capi-vibrator-type-h.md#vibrator_errorcode).|

### OH_Vibrator_PlayVibrationCustom()

```c
int32_t OH_Vibrator_PlayVibrationCustom(Vibrator_FileDescription fileDescription, Vibrator_Attribute vibrateAttribute)
```

**Description**

Configure the vibrator to vibrate with the custom sequence.

**Required permissions**: ohos.permission.VIBRATE

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [Vibrator_FileDescription](capi-vibrator-vibrator-filedescription.md) fileDescription | File descriptor of the custom vibration effect. For details, see [Vibrator_FileDescription](capi-vibrator-vibrator-filedescription.md).|
| [Vibrator_Attribute](capi-vibrator-vibrator-attribute.md) vibrateAttribute | Vibration attribute. For details, see [Vibrator_Attribute](capi-vibrator-vibrator-attribute.md).|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns **0** if the operation is successful; returns a non-zero value otherwise. For details, see [Vibrator_ErrorCode](capi-vibrator-type-h.md#vibrator_errorcode).|

### OH_Vibrator_Cancel()

```c
int32_t OH_Vibrator_Cancel()
```

**Description**

Stops the vibration.

**Required permissions**: ohos.permission.VIBRATE

**Since**: 11

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns **0** if the operation is successful; returns a non-zero value otherwise. For details, see [Vibrator_ErrorCode](capi-vibrator-type-h.md#vibrator_errorcode).|
