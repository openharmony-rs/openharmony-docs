# ArkUI_ParallelGestureEvent
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhou-chaobo-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=3b17ae247298f1cf952b1cbdcb60f1ff0e80beac translatedAt=2026-11-09T11:47:30.386Z pushedAt=2026-11-10T03:36:00.947Z nl=1 -->

```c
typedef struct ArkUI_ParallelGestureEvent ArkUI_ParallelGestureEvent
```

## Overview

Defines a parallel gesture event. This struct is passed as a parameter of the [setGestureParallelTo](capi-arkui-nativemodule-arkui-nativegestureapi-3.md#setgestureparallelto) callback function. It contains the current gesture recognizer, the conflicting gesture recognizer in the response chain, and user-defined data, for the callback to select the object that needs to be recognized in parallel with the current gesture.

**Since**: 26.0.0

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_gesture.h](capi-native-gesture-h.md)
