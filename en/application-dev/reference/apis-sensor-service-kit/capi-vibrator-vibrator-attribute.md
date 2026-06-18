# Vibrator_Attribute
<!--Kit: Sensor Service Kit-->
<!--Subsystem: Sensors-->
<!--Owner: @dilligencer-->
<!--Designer: @andeszhang-->
<!--Tester: @liuhaonan2-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=7b96ce2cdc47279f6264c88642e4fd07a8682bf6 translatedAt=2026-06-18T03:35:40.030Z pushedAt=2026-06-18T07:24:16.906Z -->

```c
typedef struct Vibrator_Attribute { ... } Vibrator_Attribute
```

## Overview

Defines the vibrator attribute.

**Since**: 11

**Related module**: [Vibrator](capi-vibrator.md)

**Header file**: [vibrator_type.h](capi-vibrator-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| int32_t vibratorId | Vibrator ID.|
| [Vibrator_Usage](capi-vibrator-type-h.md#vibrator_usage) usage | Vibration scenario.|