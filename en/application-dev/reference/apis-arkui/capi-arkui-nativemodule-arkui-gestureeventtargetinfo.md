# ArkUI_GestureEventTargetInfo
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhou-chaobo-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=3b17ae247298f1cf952b1cbdcb60f1ff0e80beac translatedAt=2026-11-09T11:42:42.056Z pushedAt=2026-11-10T02:27:11.164Z nl=1 -->

```c
typedef struct ArkUI_GestureEventTargetInfo ArkUI_GestureEventTargetInfo
```

## Overview

Defines gesture event target information, which is used to query the scroll start/end states of the gesture event target object during gesture handling. It is mainly applicable to scrollable components. You can obtain the target information from the gesture recognizer through [OH_ArkUI_GetGestureEventTargetInfo](capi-native-gesture-h.md#oh_arkui_getgestureeventtargetinfo), and read the target state through the target information query API.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_gesture.h](capi-native-gesture-h.md)

