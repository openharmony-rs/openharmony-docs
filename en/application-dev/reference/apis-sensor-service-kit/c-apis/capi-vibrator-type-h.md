# vibrator_type.h

## Overview

Declares the APIs for starting or stopping vibration.

**Library**: libohvibrator.z.so

**System capability**: SystemCapability.Sensors.MiscDevice

**Since**: 11

**Related module**: [Vibrator](capi-vibrator.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [Vibrator_Attribute](capi-vibrator-vibrator-attribute.md) | Vibrator_Attribute | Defines the vibrator attribute. |
| [Vibrator_FileDescription](capi-vibrator-vibrator-filedescription.md) | Vibrator_FileDescription | Defines the vibration file description. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [Vibrator_ErrorCode](#vibrator_errorcode) | Vibrator_ErrorCode | Enumerates the vibrator error codes. |
| [Vibrator_Usage](#vibrator_usage) | Vibrator_Usage | Enumerates the vibration scenarios. |

## Enum type description

### Vibrator_ErrorCode

```c
enum Vibrator_ErrorCode
```

**Description**

Enumerates the vibrator error codes.

**Since**: 11

| Enum item | Description |
| -- | -- |
| PERMISSION_DENIED = 201 | < @error Permission verification failed. |
| PARAMETER_ERROR = 401 | < Parameter check failed. For example, a mandatory parameter is not passed in, |
| UNSUPPORTED = 801 | < The API is not supported on the device. The device supports the corresponding SysCap, |
| DEVICE_OPERATION_FAILED = 14600101 | < @error The operation on the device failed. |

### Vibrator_Usage

```c
enum Vibrator_Usage
```

**Description**

Enumerates the vibration scenarios.

**Since**: 11

| Enum item | Description |
| -- | -- |
| VIBRATOR_USAGE_UNKNOWN = 0 | Unknown scenario |
| VIBRATOR_USAGE_ALARM = 1 | Alarming |
| VIBRATOR_USAGE_RING = 2 | Ringing |
| VIBRATOR_USAGE_NOTIFICATION = 3 | Notification |
| VIBRATOR_USAGE_COMMUNICATION = 4 | Telecommunications |
| VIBRATOR_USAGE_TOUCH = 5 | Touch |
| VIBRATOR_USAGE_MEDIA = 6 | Multimedia |
| VIBRATOR_USAGE_PHYSICAL_FEEDBACK = 7 | Physical feedback |
| VIBRATOR_USAGE_SIMULATED_REALITY = 8 | Simulated reality |


