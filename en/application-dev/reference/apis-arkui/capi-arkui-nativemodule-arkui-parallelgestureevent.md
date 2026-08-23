# ArkUI_ParallelGestureEvent

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=307c96700aa31ceaed2d16437f8e9e4fabcbd960 translatedAt=2026-08-19T08:26:58.044Z pushedAt=2026-08-20T06:07:16.972Z -->

```c
typedef struct ArkUI_ParallelGestureEvent ArkUI_ParallelGestureEvent
```

## Overview

Defines a parallel gesture event. This struct is passed as a parameter of the [setGestureParallelTo](capi-arkui-nativemodule-arkui-nativegestureapi-3.md#setgestureparallelto) callback function. It contains the current gesture recognizer, the conflicting gesture recognizer in the response chain, and user-defined data, for the callback to select the object that needs to be recognized in parallel with the current gesture.

**Since**: 26.0.0

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_gesture.h](capi-native-gesture-h.md)