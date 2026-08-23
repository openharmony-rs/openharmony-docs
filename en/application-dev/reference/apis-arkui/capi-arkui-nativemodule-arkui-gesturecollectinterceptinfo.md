# ArkUI_GestureCollectInterceptInfo

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=307c96700aa31ceaed2d16437f8e9e4fabcbd960 translatedAt=2026-08-19T04:18:00.407Z pushedAt=2026-08-19T07:41:00.830Z -->

```c
typedef struct ArkUI_GestureCollectInterceptInfo ArkUI_GestureCollectInterceptInfo
```

## Overview

Defines gesture collection interception information. During gesture collection in the touch test, this struct is used to provide the gesture and touch recognizers in the response chain to the interception callback, and carries the gesture collection intervention result set by the callback. For details about the related APIs for gesture collection interception, see [native_gesture.h](capi-native-gesture-h.md).

**Since**: 26.0.0

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_type.h](capi-native-type-h.md)