# ArkUI_GestureEvent
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhou-chaobo-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=3b17ae247298f1cf952b1cbdcb60f1ff0e80beac translatedAt=2026-11-09T11:42:18.005Z pushedAt=2026-11-10T02:18:54.389Z nl=1 -->

```c
typedef struct ArkUI_GestureEvent ArkUI_GestureEvent
```

## Overview

Defines the object of gesture event data, which is used to carry and transfer gesture event-related data during gesture event processing. It supports obtaining key information such as the gesture event type, coordinates, and timestamp. This struct is applicable to scenarios that require processing touch gesture interactions, such as tap, long-pressing, drag, and pinch gesture recognition and response. You can obtain event information through related gesture event APIs.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_gesture.h](capi-native-gesture-h.md)

