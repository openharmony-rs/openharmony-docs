# ArkUI_GestureEventTargetInfo

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=307c96700aa31ceaed2d16437f8e9e4fabcbd960 translatedAt=2026-08-19T08:23:24.060Z pushedAt=2026-08-19T09:02:54.227Z -->

```c
typedef struct ArkUI_GestureEventTargetInfo ArkUI_GestureEventTargetInfo
```

## Overview

Defines gesture event target information. This struct is used to query the status of the gesture event target object, such as scroll start and scroll end, during gesture processing. It is mainly applicable to scrollable container components. You can obtain this object from the gesture recognizer through [OH_ArkUI_GetGestureEventTargetInfo](capi-native-gesture-h.md#oh_arkui_getgestureeventtargetinfo), and read the target status through the target information query API.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_gesture.h](capi-native-gesture-h.md)