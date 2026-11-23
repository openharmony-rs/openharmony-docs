# ArkUI_GestureRecognizer
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhou-chaobo-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=3b17ae247298f1cf952b1cbdcb60f1ff0e80beac translatedAt=2026-11-09T11:42:46.423Z pushedAt=2026-11-10T02:33:24.195Z nl=1 -->

```c
typedef struct ArkUI_GestureRecognizer ArkUI_GestureRecognizer
```

## Overview

Defines a gesture recognizer instance object, which is used to represent a gesture recognizer object in ArkUI gesture recognition APIs. After being bound to a UI component, the gesture recognizer listens for touch events and notifies you through a callback when the recognition conditions of the corresponding gesture type are met. Different types of recognizers can be used for gestures such as tap, long press, drag, pinch, rotation, and swipe. For details about the mechanism and usage, see the gesture API description in [native_gesture.h](capi-native-gesture-h.md).

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_gesture.h](capi-native-gesture-h.md)

