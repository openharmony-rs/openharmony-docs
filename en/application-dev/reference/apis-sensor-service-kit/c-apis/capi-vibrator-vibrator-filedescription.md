# Vibrator_FileDescription

```c
typedef struct Vibrator_FileDescription {...} Vibrator_FileDescription
```

## Overview

Defines the vibration file description.

**Since**: 11

**Related module**: [Vibrator](capi-vibrator.md)

**Header file**: [vibrator_type.h](capi-vibrator-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t fd | < File handle of the custom vibration sequence. |
| int64_t offset | < Offset address of the custom vibration sequence. |
| int64_t length | < Total length of the custom vibration sequence. |


