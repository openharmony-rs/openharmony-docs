# ArkUI_GestureInterruptInfo

```c
typedef struct ArkUI_GestureInterruptInfo ArkUI_GestureInterruptInfo
```

## Overview

Defines gesture interruption event information. This struct is used to pass information such as the gesture recognizer, response chain gesture recognizer, and touch recognizer to the gesture interruption callback. The callback can return a continue or reject result based on this information. For details about the gesture interruption mechanism and APIs, see the gesture interruption API description in native_gesture.h.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_gesture.h](capi-native-gesture-h.md)

