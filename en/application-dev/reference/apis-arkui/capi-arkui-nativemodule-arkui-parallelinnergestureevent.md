# ArkUI_ParallelInnerGestureEvent
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=177cf08b41b42ef2a0a1e73e96f1ea583ec5a150 translatedAt=2026-09-20T09:23:29.118Z pushedAt=2026-09-22T08:49:43.040Z -->

```c
typedef struct ArkUI_ParallelInnerGestureEvent ArkUI_ParallelInnerGestureEvent
```

## Overview

Defines a parallel inner gesture event. This struct is passed as a parameter of the [setInnerGestureParallelTo](capi-arkui-nativemodule-arkui-nativegestureapi-1.md#setinnergestureparallelto) callback function. It is used in scenarios where a system built-in gesture (such as the built-in sliding gesture of container components like **Scroll** and **List**) is set to be parallel with other components in the response chain.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_gesture.h](capi-native-gesture-h.md)
