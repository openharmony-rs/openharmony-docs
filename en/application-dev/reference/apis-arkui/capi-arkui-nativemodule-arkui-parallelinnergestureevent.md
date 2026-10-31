# ArkUI_ParallelInnerGestureEvent

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=307c96700aa31ceaed2d16437f8e9e4fabcbd960 translatedAt=2026-08-19T08:27:02.632Z pushedAt=2026-08-20T06:08:53.603Z -->

```c
typedef struct ArkUI_ParallelInnerGestureEvent ArkUI_ParallelInnerGestureEvent
```

## Overview

Defines a parallel inner gesture event. This struct is passed as a parameter of the [setInnerGestureParallelTo](capi-arkui-nativemodule-arkui-nativegestureapi-1.md#setinnergestureparallelto) callback function. It contains the current built-in gesture recognizer, the conflicting gesture recognizer in the response chain, and user-defined data, so that the callback can select the object to be recognized in parallel with the current built-in gesture.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_gesture.h](capi-native-gesture-h.md)