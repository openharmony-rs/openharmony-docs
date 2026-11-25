# ArkUI_GestureEvent
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhou-chaobo-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=9c92183287fa23162e04874223c3b068eb1f8a4d translatedAt=2026-11-23T07:04:11.286Z pushedAt=2026-11-24T09:22:56.930Z nl=1 -->

```c
typedef struct ArkUI_GestureEvent ArkUI_GestureEvent
```

## Overview

Defines the object of gesture event data, which is used to carry and transfer gesture event-related data during gesture event processing. It supports obtaining key information such as the gesture event type, coordinates, and timestamp. This struct is applicable to scenarios that require processing touch gesture interactions, such as tap, long-pressing, drag, and pinch gesture recognition and response. You can obtain event information through related gesture event APIs.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_gesture.h](capi-native-gesture-h.md)

