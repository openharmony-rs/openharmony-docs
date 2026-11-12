# ArkUI_GestureInterruptInfo
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhou-chaobo-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=3b17ae247298f1cf952b1cbdcb60f1ff0e80beac translatedAt=2026-11-09T11:42:38.037Z pushedAt=2026-11-10T02:27:18.106Z nl=1 -->

```c
typedef struct ArkUI_GestureInterruptInfo ArkUI_GestureInterruptInfo
```

## Overview

Defines gesture interruption event information. This struct is used to pass information such as the gesture recognizer, response chain gesture recognizer, and touch recognizer to the gesture interruption callback. The callback can return a continue or reject result based on this information. For details about the gesture interruption mechanism and APIs, see the gesture interruption API description in [native_gesture.h](capi-native-gesture-h.md).

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_gesture.h](capi-native-gesture-h.md)

