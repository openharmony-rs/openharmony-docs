# OH_AudioObjectPosition
<!--Kit: AVCodec Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @mr-chencxy-->
<!--Designer: @dpy2650--->
<!--Tester: @baotianhao-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct OH_AudioObjectPosition {...} OH_AudioObjectPosition
```

## Overview

This struct describes the position of an audio object source in three-dimensional space. The position can be expressed using either Cartesian coordinates or polar coordinates.

**Since:** 26.0.0

**Related module:** [Core](capi-core.md)

**Header file:** [native_audio_vivid.h](capi-native-audio-vivid-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| bool isCartesian | Whether the audio object source is represented using Cartesian coordinates. <br>The value **true** indicates that Cartesian coordinates are used, and the value **false** indicates that polar coordinates are used.|
| union {<br>[OH_CartesianPosition](capi-core-oh-cartesianposition.md) cartesian;<br>[OH_PolarPosition](capi-core-oh-polarposition.md) polar; <br>} pos | Union that contains the position data, which can be either Cartesian coordinates or polar coordinates.<br>**cartesian**: position represented in Cartesian coordinates.<br>**polar**: position represented in polar coordinates.|
