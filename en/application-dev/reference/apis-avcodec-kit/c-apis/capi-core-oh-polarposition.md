# OH_PolarPosition

```c
typedef struct OH_PolarPosition {...} OH_PolarPosition
```

## Overview

Represents a position in polar (spherical) coordinates.<br> Polar coordinates use azimuth, elevation, and distance to define a position in three-dimensional space.

**System capability**: SystemCapability.Multimedia.Media.Core

**Since**: 26.0.0

**Related module**: [Core](capi-core.md)

**Header file**: [native_audio_vivid.h](capi-native-audio-vivid-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| float azimuth | Indicates the azimuth angle of the object's location when the polar coordinate system is used.<br> Value range is [-180.0, 180.0], where 0.0 is front, 90.0 is left, -90.0 is right, -180.0 or 180.0 is back.<br>**Since**: 26.0.0 |
| float elevation | Indicates the elevation angle of the object's location when the polar coordinate system is used.<br> Value range is [-90.0, 90.0], where 0.0 is horizontal, 90.0 is up, -90.0 is down.<br>**Since**: 26.0.0 |
| float distance | Normalized distance of an object's location when an object is placed in the polar coordinate system.<br> Value range is [0.0, 1.0].<br>**Since**: 26.0.0 |


