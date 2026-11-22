# ArkUI_ParallelInnerGestureEvent
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhou-chaobo-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=3b17ae247298f1cf952b1cbdcb60f1ff0e80beac translatedAt=2026-11-09T11:47:33.106Z pushedAt=2026-11-10T03:36:04.730Z nl=1 -->

```c
typedef struct ArkUI_ParallelInnerGestureEvent ArkUI_ParallelInnerGestureEvent
```

## Overview

Defines a parallel inner gesture event. This struct is passed as a parameter of the [setInnerGestureParallelTo](capi-arkui-nativemodule-arkui-nativegestureapi-1.md#setinnergestureparallelto) callback function. It contains the current built-in gesture recognizer, the conflicting gesture recognizer in the response chain, and user-defined data, so that the callback can select the object to be recognized in parallel with the current built-in gesture.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_gesture.h](capi-native-gesture-h.md)
