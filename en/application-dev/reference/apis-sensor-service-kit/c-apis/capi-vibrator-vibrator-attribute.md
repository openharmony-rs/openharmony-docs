# Vibrator_Attribute

```c
struct Vibrator_Attribute {...}
```

## Overview

The **Vibrator_Attribute** struct is used to describe the attributes of the vibrator. You can use this struct to specify the vibrator ID and vibration scenario. For details about the application scenarios and implementation mechanism, see the Vibrator module documentation.

**System capability**: SystemCapability.Sensors.MiscDevice

**Since**: 11

**Related module**: [Vibrator](capi-vibrator.md)

**Header file**: [vibrator_type.h](capi-vibrator-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t vibratorId | Vibrator ID. Its value is obtained through the system API. This is the ID of the vibrator to be * operated. Different IDs correspond to different vibrators on the device. The value range is * [0, Maximum number of supported vibrators – 1]. |
| [Vibrator_Usage](capi-vibrator-type-h.md#vibrator_usage) usage | Vibration scenario. This parameter specifies the application scenario of the vibrator. Different * scenarios correspond to different vibration modes. For example, notifications, buttons, and alarm clocks have * their own vibration effects. For details about the options, see the **Vibrator_Usage** enumeration. |


