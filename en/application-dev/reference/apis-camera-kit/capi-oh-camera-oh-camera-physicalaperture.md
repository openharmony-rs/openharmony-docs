# OH_Camera_PhysicalAperture
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct OH_Camera_PhysicalAperture {...} OH_Camera_PhysicalAperture
```

## Overview

Physical aperture configuration.

**Since**: 24

**Related module**: [OH_Camera](capi-oh-camera.md)

**Header file**: [camera.h](capi-camera-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [OH_Camera_ZoomRange](capi-oh-camera-oh-camera-zoomrange.md) zoomRange | Zoom range.|
| float* apertures | Array of supported aperture values.|
| size_t apertureCount | Number of aperture values.|
