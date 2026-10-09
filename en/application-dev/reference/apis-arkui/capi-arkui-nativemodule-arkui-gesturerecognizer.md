# ArkUI_GestureRecognizer

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=307c96700aa31ceaed2d16437f8e9e4fabcbd960 translatedAt=2026-08-19T08:23:29.586Z pushedAt=2026-08-19T09:13:51.916Z -->

```c
typedef struct ArkUI_GestureRecognizer ArkUI_GestureRecognizer
```

## Overview

Defines a gesture component object, which is used to represent a gesture recognizer object in the ArkUI gesture recognition APIs. After a gesture recognizer is bound to a UI component, it listens for touch events and notifies you through a callback when the recognition conditions of the corresponding gesture type are met. Different types of recognizers can be used for gestures such as tap, long press, pan, pinch, rotation, and swipe. For details about the mechanism and usage, see the gesture API description in [native_gesture.h](capi-native-gesture-h.md).

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_gesture.h](capi-native-gesture-h.md)