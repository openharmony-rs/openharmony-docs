# ArkUI_ParallelGestureEvent
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhou-chaobo-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=9c92183287fa23162e04874223c3b068eb1f8a4d translatedAt=2026-11-23T07:07:40.188Z pushedAt=2026-11-25T01:16:45.268Z nl=1 -->

```c
typedef struct ArkUI_ParallelGestureEvent ArkUI_ParallelGestureEvent
```

## Overview

Defines a parallel gesture event. This struct is passed as a parameter of the [setGestureParallelTo](capi-arkui-nativemodule-arkui-nativegestureapi-3.md#setgestureparallelto) callback function. It is used to set a parallel relationship between your custom gesture and the gestures of other components in the response chain when a touch test is triggered.

**Since**: 26.0.0

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_gesture.h](capi-native-gesture-h.md)
