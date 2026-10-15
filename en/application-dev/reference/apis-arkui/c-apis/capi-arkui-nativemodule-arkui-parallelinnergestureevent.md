# ArkUI_ParallelInnerGestureEvent

```c
typedef struct ArkUI_ParallelInnerGestureEvent ArkUI_ParallelInnerGestureEvent
```

## Overview

Defines a parallel inner gesture event. This struct is passed as a parameter of the [setInnerGestureParallelTo](capi-arkui-nativemodule-arkui-nativegestureapi-1.md#setinnergestureparallelto) callback function. It contains the current built-in gesture recognizer, the conflicting gesture recognizer in the response chain, and user-defined data, so that the callback can select the object to be recognized in parallel with the current built-in gesture.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_gesture.h](capi-native-gesture-h.md)

