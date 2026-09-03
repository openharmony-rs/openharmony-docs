# ArkUI_GestureInterruptInfo

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=307c96700aa31ceaed2d16437f8e9e4fabcbd960 translatedAt=2026-08-19T08:23:27.822Z pushedAt=2026-08-19T09:04:59.021Z -->

```c
typedef struct ArkUI_GestureInterruptInfo ArkUI_GestureInterruptInfo
```

## Overview

Defines gesture interruption event information. This struct is used to pass information such as the gesture recognizer, response chain gesture recognizer, and touch recognizer to the gesture interruption callback. The callback can return a continue or reject result based on this information. For details about the gesture interruption mechanism and APIs, see the gesture interruption API description in [native_gesture.h](capi-native-gesture-h.md).

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_gesture.h](capi-native-gesture-h.md)