# ArkUI_GestureEvent

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=f8ecdb82f3ec053eb7dde21e27a6f047d194898a translatedAt=2026-07-17T09:23:55.278Z pushedAt=2026-07-17T10:45:30.797Z -->

```c
typedef struct ArkUI_GestureEvent ArkUI_GestureEvent
```

## Overview

Defines the object of gesture event data, which is used to carry and transfer gesture event-related data during gesture event processing. It supports obtaining key information such as the gesture event type, coordinates, and timestamp. This struct is applicable to scenarios that require processing touch gesture interactions, such as tap, long-pressing, drag, and pinch gesture recognition and response. You can obtain event information through related gesture event APIs.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_gesture.h](capi-native-gesture-h.md)