# Vibrator_Attribute
<!--Kit: Sensor Service Kit-->
<!--Subsystem: Sensors-->
<!--Owner: @dilligencer-->
<!--Designer: @andeszhang-->
<!--Tester: @zhaofangyuan-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=2cc3d788470dfc527ff67f0d956b9e3149129ee5 translatedAt=2026-09-02T07:32:58.411Z pushedAt=2026-09-06T06:02:38.982Z -->

```c
typedef struct Vibrator_Attribute { ... } Vibrator_Attribute
```

## Overview

The **Vibrator_Attribute** struct is used to describe the attributes of the vibrator. You can use this struct to specify the vibrator ID and vibration scenario. For details about the application scenarios and implementation mechanism, see the [Vibrator](capi-vibrator.md) module documentation.

**Since**: 11

**Related module**: [Vibrator](capi-vibrator.md)

**Header file**: [vibrator_type.h](capi-vibrator-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| int32_t vibratorId | Vibrator ID. Its value is obtained through the system API. This is the ID of the vibrator to be operated. Different IDs correspond to different vibrators on the device. The value range is [0, Maximum number of supported vibrators – 1]. |
| [Vibrator_Usage](capi-vibrator-type-h.md#vibrator_usage) usage | Vibration scenario. This parameter specifies the application scenario of the vibrator. Different scenarios correspond to different vibration modes. For example, notifications, buttons, and alarm clocks have their own vibration effects. For details about the options, see the **Vibrator_Usage** enumeration. |