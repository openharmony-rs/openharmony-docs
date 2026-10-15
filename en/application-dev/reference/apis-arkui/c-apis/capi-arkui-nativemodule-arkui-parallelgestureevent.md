# ArkUI_ParallelGestureEvent

```c
typedef struct ArkUI_ParallelGestureEvent ArkUI_ParallelGestureEvent
```

## Overview

Defines a parallel gesture event. This struct is passed as a parameter of the [setGestureParallelTo](capi-arkui-nativemodule-arkui-nativegestureapi-3.md#setgestureparallelto) callback function. It contains the current gesture recognizer, the conflicting gesture recognizer in the response chain, and user-defined data, for the callback to select the object that needs to be recognized in parallel with the current gesture.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_gesture.h](capi-native-gesture-h.md)

