# OH_PolarPosition
<!--Kit: AVCodec Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @mr-chencxy-->
<!--Designer: @dpy2650--->
<!--Tester: @baotianhao-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct OH_PolarPosition {...} OH_PolarPosition
```

## Overview

This struct describes a position in the polar coordinate system (also known as the spherical coordinate system). The polar coordinate system uses the azimuth, elevation, and distance to define the position of an audio object source in three-dimensional space.

**Since:** 26.0.0

**Related module:** [Core](capi-core.md)

**Header file:** [native_audio_vivid.h](capi-native-audio-vivid-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| float azimuth | Azimuth of the position where the audio object source is located in the polar coordinate system.<br> The value range is [-180.0, 180.0], where **0.0** represents straight ahead, **90.0** represents left, **-90.0** represents right, and **-180.0** or **180.0** represents directly behind.|
| float elevation | Elevation of the position where the audio object source is located in the polar coordinate system.<br> The value range is [-90.0, 90.0], where **0.0** represents horizontal, **90.0** represents directly above, and **-90.0** represents directly below.|
| float distance | Normalized distance of the position where the audio object source is located in the polar coordinate system.<br> The value range is [0.0, 1.0].|
