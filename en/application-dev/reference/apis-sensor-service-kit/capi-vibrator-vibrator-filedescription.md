# Vibrator_FileDescription
<!--Kit: Sensor Service Kit-->
<!--Subsystem: Sensors-->
<!--Owner: @dilligencer-->
<!--Designer: @andeszhang-->
<!--Tester: @liuhaonan2-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=7b96ce2cdc47279f6264c88642e4fd07a8682bf6 translatedAt=2026-06-18T03:35:44.025Z pushedAt=2026-06-18T07:24:16.910Z -->

```c
typedef struct Vibrator_FileDescription { ... } Vibrator_FileDescription
```

## Overview

Defines the vibration file description.

**Since**: 11

**Related module**: [Vibrator](capi-vibrator.md)

**Header file**: [vibrator_type.h](capi-vibrator-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| int32_t fd | File handle of the custom vibration sequence.|
| int64_t offset | Offset address of the custom vibration sequence.|
| int64_t length | Total length of the custom vibration sequence.|