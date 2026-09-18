# OH_AudioObjectPosition

```c
typedef struct OH_AudioObjectPosition {...} OH_AudioObjectPosition
```

## Overview

Represents the position of an audio object in three-dimensional space.<br> The position can be expressed in either Cartesian or polar coordinates.

**Since**: 26.0.0

**Related module**: [Core](capi-core.md)

**Header file**: [native_audio_vivid.h](capi-native-audio-vivid-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| bool isCartesian | Indicates whether the position is in Cartesian coordinates.<br> true: use pos.cartesian, false: use pos.polar.<br>**Since**: 26.0.0 |
| union | Union containing the position data in either Cartesian or polar coordinates.<br>**Since**: 26.0.0 |
| [OH_CartesianPosition](capi-core-oh-cartesianposition.md) cartesian | Represents position by Cartesian coordinates.<br>**Since**: 26.0.0 |
| OH_PolarPosition polar;
 } pos | Represents position by polar coordinates.<br>**Since**: 26.0.0 |


