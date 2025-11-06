# vibrator_type.h
<!--Kit: Sensor Service Kit-->
<!--Subsystem: Sensors-->
<!--Owner: @dilligencer-->
<!--Designer: @butterls-->
<!--Tester: @murphy84-->
<!--Adviser: @hu-zhiqiong-->

## Overview

Defines the structs for the vibrator attribute and vibrator file description and provides the enums for error codes and vibration scenarios.

**Reference file**: <sensors/vibrator_type.h>

**Library**: libohvibrator.z.so

**System capability**: SystemCapability.Sensors.MiscDevice

**Since**: 11

**Related module**: [Vibrator](capi-vibrator.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [Vibrator_Attribute](capi-vibrator-vibrator-attribute.md) | Vibrator_Attribute | Defines a struct for the vibrator attribute.|
| [Vibrator_FileDescription](capi-vibrator-vibrator-filedescription.md) | Vibrator_FileDescription | Defines a struct for the vibration file description.|

### Enumeration

| API| typedef Keyword| Description|
| -- | -- | -- |
| [Vibrator_ErrorCode](#vibrator_errorcode) | Vibrator_ErrorCode | Enumerates the vibrator error codes.|
| [Vibrator_Usage](#vibrator_usage) | Vibrator_Usage | Enumerates the vibration scenarios.|

## Enum Description

### Vibrator_ErrorCode

```
enum Vibrator_ErrorCode
```

**Description**

Enumerates the vibrator error codes.

**Since**: 11

| Enum Item| Description|
| -- | -- |
| PERMISSION_DENIED = 201 | Permission denied.|
| PARAMETER_ERROR = 401 | Parameter check failed. For example, a mandatory parameter is not passed in, or the parameter type passed in is incorrect.|
| UNSUPPORTED = 801 | The device does not support this API. Generally, this enumerated value is used for a device that supports the corresponding system capability but only parts of APIs.|
| DEVICE_OPERATION_FAILED = 14600101 | Device operation failed.|

### Vibrator_Usage

```
enum Vibrator_Usage
```

**Description**

Enumerates the vibration scenarios.

**Since**: 11

| Enum Item| Description|
| -- | -- |
| USAGE_UNKNOWN = 0 | Unknown scenario|
| USAGE_ALARM = 1 | Alarming|
| USAGE_RING = 2 | Ringing|
| USAGE_NOTIFICATION = 3 | Notification|
| USAGE_COMMUNICATION = 4 | Telecommunications|
| USAGE_TOUCH = 5 | Touch|
| USAGE_MEDIA = 6 | Multimedia|
| USAGE_PHYSICAL_FEEDBACK = 7 | Physical feedback|
| USAGE_SIMULATE_REALITY = 8 | Simulated reality|
