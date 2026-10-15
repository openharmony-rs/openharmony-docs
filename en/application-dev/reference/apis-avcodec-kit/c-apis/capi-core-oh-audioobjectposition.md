# OH_AudioObjectPosition

```c
struct OH_AudioObjectPosition {...}
```

## Overview

Represents the position of an audio object in three-dimensional space.<br> The position can be expressed in either Cartesian or polar coordinates.

**System capability**: SystemCapability.Multimedia.Media.Core

**Since**: 26.0.0

**Related module**: [Core](capi-core.md)

**Header file**: [native_audio_vivid.h](capi-native-audio-vivid-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| bool isCartesian | Indicates whether the position is in Cartesian coordinates.<br> true: use pos.cartesian, false: use pos.polar.<br>**Since**: 26.0.0 |
| pos.cartesian | Represents position by Cartesian coordinates.<br>**Since**: 26.0.0 |
| pos.polar | Represents position by polar coordinates.<br>**Since**: 26.0.0 |


