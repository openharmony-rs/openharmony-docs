# vibrator_type.h
<!--Kit: Sensor Service Kit-->
<!--Subsystem: Sensors-->
<!--Owner: @dilligencer-->
<!--Designer: @butterls-->
<!--Tester: @murphy84-->
<!--Adviser: @hu-zhiqiong-->

## Overview

The **vibrator_type.h** file declares the APIs for starting or stopping vibration.

**Library**: libohvibrator.z.so

**System capability**: SystemCapability.Sensors.MiscDevice

**Since**: 11

**Related module**: [Vibrator](_vibrator.md)


## Summary


### Structs

| Name| Description|
| -------- | -------- |
| [Vibrator_Attribute](_vibrator_attribute.md) | Defines a struct for the vibrator attribute. |
| [Vibrator_FileDescription](_vibrator_file_description.md) | Defines a struct for the vibration file description. |


### Types

| Name| Description|
| -------- | -------- |
| [Vibrator_ErrorCode](_vibrator.md#vibrator_errorcode) | Enumerates the vibrator error codes. |
| [Vibrator_Usage](_vibrator.md#vibrator_usage) | Enumerates the vibration scenarios. |
| [Vibrator_Attribute](_vibrator.md#vibrator_attribute) | Defines a struct for the vibrator attribute. |
| [Vibrator_FileDescription](_vibrator.md#vibrator_filedescription) | Defines a struct for the vibration file description. |


### Enums

| Name| Description|
| -------- | -------- |
| [Vibrator_ErrorCode](_vibrator.md#vibrator_errorcode) : int32_t {<br>PERMISSION_DENIED = 201<br>PARAMETER_ERROR = 401, <br>[UNSUPPORTED] = 801, <br>[DEVICE_OPERATION_FAILED = 14600101<br>} | Enumerates the vibrator error codes. |
| [Vibrator_Usage](_vibrator.md#vibrator_usage) {<br>USAGE_UNKNOWN = 0, <br>USAGE_ALARM = 1, <br>USAGE_RING = 2,<br>USAGE_NOTIFICATION = 3,<br>USAGE_COMMUNICATION = 4,<br>USAGE_TOUCH = 5, <br>USAGE_MEDIA = 6, <br>USAGE_PHYSICAL_FEEDBACK = 7,<br>USAGE_SIMULATE_REALITY = 8, <br>USAGE_MAX = 9<br>} | Enumerates the vibration scenarios. |
