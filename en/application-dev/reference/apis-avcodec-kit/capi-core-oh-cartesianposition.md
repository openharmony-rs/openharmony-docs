# OH_CartesianPosition
<!--Kit: AVCodec Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @mr-chencxy-->
<!--Designer: @dpy2650--->
<!--Tester: @baotianhao-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct OH_CartesianPosition {...} OH_CartesianPosition
```

## Overview

This struct describes the position of an audio object source in the Cartesian coordinate system. The Cartesian coordinate system uses the X, Y, and Z axes to define a position in three-dimensional space.

**Since:** 26.0.0

**Related module:** [Core](capi-core.md)

**Header file:** [native_audio_vivid.h](capi-native-audio-vivid-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| float x | Normalized X coordinate of the audio object source in the Cartesian coordinate system, representing the left/right dimension.<br> The value range is [-1.0, 1.0].|
| float y | Normalized Y coordinate of the audio object source in the Cartesian coordinate system, representing the front/back dimension<br> The value range is [-1.0, 1.0].|
| float z | Normalized Z coordinate of the audio object source in the Cartesian coordinate system, representing the up/down dimension<br> The value range is [-1.0, 1.0].|
