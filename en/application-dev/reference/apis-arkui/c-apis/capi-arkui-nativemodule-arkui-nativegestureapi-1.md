# ArkUI_NativeGestureAPI_1

```c
typedef struct ArkUI_NativeGestureAPI_1 {...} ArkUI_NativeGestureAPI_1
```

## Overview

Defines the gesture APIs.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_gesture.h](capi-native-gesture-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t version | The struct version is 1. |


### Member functions

| Name | Description |
| -- | -- |
| [ArkUI_GestureRecognizer* (\*createTapGesture)(int32_t countNum, int32_t fingersNum)](#createtapgesture) | Creates a tap gesture. |
| [ArkUI_GestureRecognizer* (\*createLongPressGesture)(int32_t fingersNum, bool repeatResult, int32_t durationNum)](#createlongpressgesture) | Creates a long press gesture. |
| [ArkUI_GestureRecognizer* (\*createPanGesture)(int32_t fingersNum, ArkUI_GestureDirectionMask directions, double distanceNum)](#createpangesture) | Creates a swipe gesture. |
| [ArkUI_GestureRecognizer* (\*createPinchGesture)(int32_t fingersNum, double distanceNum)](#createpinchgesture) | Creates a pinch gesture. |
| [ArkUI_GestureRecognizer* (\*createRotationGesture)(int32_t fingersNum, double angleNum)](#createrotationgesture) | Creates a rotation gesture. |
| [ArkUI_GestureRecognizer* (\*createSwipeGesture)(int32_t fingersNum, ArkUI_GestureDirectionMask directions, double speedNum)](#createswipegesture) | Creates a swipe gesture.This API is used to implement a swipe gesture, which can be recognized when the swipe speed (px/s) is higher than that specified by **speedNum**. |
| [ArkUI_GestureRecognizer* (\*createGroupGesture)(ArkUI_GroupGestureMode gestureMode)](#creategroupgesture) | Creates a gesture group. |
| [void (\*dispose)(ArkUI_GestureRecognizer* recognizer)](#dispose) | Disposes of a gesture to release resources. |
| [int32_t (\*addChildGesture)(ArkUI_GestureRecognizer* group, ArkUI_GestureRecognizer* child)](#addchildgesture) | Adds a gesture to a gesture group. |
| [int32_t (\*removeChildGesture)(ArkUI_GestureRecognizer* group, ArkUI_GestureRecognizer* child)](#removechildgesture) | Removes a gesture from a gesture group. |
| [int32_t (\*setGestureEventTarget)(ArkUI_GestureRecognizer* recognizer, ArkUI_GestureEventActionTypeMask actionTypeMask, void* extraParams,void (\*targetReceiver)(ArkUI_GestureEvent* event, void* extraParams))](#setgestureeventtarget) | Registers a callback for gestures. |
| [int32_t (\*addGestureToNode)(ArkUI_NodeHandle node, ArkUI_GestureRecognizer* recognizer, ArkUI_GesturePriority mode, ArkUI_GestureMask mask)](#addgesturetonode) | Adds a gesture to a UI component. |
| [int32_t (\*removeGestureFromNode)(ArkUI_NodeHandle node, ArkUI_GestureRecognizer* recognizer)](#removegesturefromnode) | Removes a gesture from a node. |
| [int32_t (\*setGestureInterrupterToNode)(ArkUI_NodeHandle node, ArkUI_GestureInterruptResult (\*interrupter)(ArkUI_GestureInterruptInfo* info))](#setgestureinterruptertonode) | Sets a gesture interruption callback for a node. |
| [ArkUI_GestureRecognizerType (\*getGestureType)(ArkUI_GestureRecognizer* recognizer)](#getgesturetype) | Obtains the type of a gesture. |
| [int32_t (\*setInnerGestureParallelTo)(ArkUI_NodeHandle node, void* userData, ArkUI_GestureRecognizer* (\*parallelInnerGesture)(ArkUI_ParallelInnerGestureEvent* event))](#setinnergestureparallelto) | Sets the callback function for the parallel internal gesture event. |
| [ArkUI_GestureRecognizer* (\*createTapGestureWithDistanceThreshold)(int32_t countNum, int32_t fingersNum, double distanceThreshold)](#createtapgesturewithdistancethreshold) | Creates a tap gesture that is subject to distance restrictions. |

## Member function description

### createTapGesture()

```c
ArkUI_GestureRecognizer* (*createTapGesture)(int32_t countNum, int32_t fingersNum)
```

**Description**

Creates a tap gesture.

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t countNum | Number of consecutive taps. If the value is less than 1 or is not set, the default value **1** is used. |
|  int32_t fingersNum | Number of fingers required to trigger the tap gesture. The value ranges from 1 to 10. If the value is less than 1 or is not set, the default value **1** is used. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_GestureRecognizer*](capi-arkui-nativemodule-arkui-gesturerecognizer.md) | Returns the pointer to the created gesture. |

### createLongPressGesture()

```c
ArkUI_GestureRecognizer* (*createLongPressGesture)(int32_t fingersNum, bool repeatResult, int32_t durationNum)
```

**Description**

Creates a long press gesture.

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t fingersNum | Minimum number of fingers to trigger a long press gesture. The value ranges from 1 to 10. If the value is out of the range, the default value **1** is used. |
|  bool repeatResult | Whether to continuously trigger the event callback. <br>The value **true** means to continuously trigger event callbacks, and **false** means the opposite. |
|  int32_t durationNum | Minimum hold-down time, in ms. If the value is less than or equal to 0, the default value **<br>500** is used. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_GestureRecognizer*](capi-arkui-nativemodule-arkui-gesturerecognizer.md) | Returns the pointer to the created gesture. |

### createPanGesture()

```c
ArkUI_GestureRecognizer* (*createPanGesture)(int32_t fingersNum, ArkUI_GestureDirectionMask directions, double distanceNum)
```

**Description**

Creates a swipe gesture.

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t fingersNum | Minimum number of fingers to trigger a pan gesture. The value ranges from 1 to 10. If the value is less than 1 or is not set, the default value **1** is used. |
|  ArkUI_GestureDirectionMask directions | Pan direction. The value supports the AND (&) and OR (\|) operations. |
|  double distanceNum | Minimum pan distance to trigger the gesture, in px. If this parameter is set to a value less than or equal to 0, the default value **5px** is used. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_GestureRecognizer*](capi-arkui-nativemodule-arkui-gesturerecognizer.md) | Pointer to the created gesture. |

### createPinchGesture()

```c
ArkUI_GestureRecognizer* (*createPinchGesture)(int32_t fingersNum, double distanceNum)
```

**Description**

Creates a pinch gesture.

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t fingersNum | Minimum number of fingers required to trigger the pinch gesture. The value ranges from 2 to 5. If the value is out of the range, the default value **2** is used. |
|  double distanceNum | Minimum recognition distance, in px. If this parameter is set to a value less than or equal to 0, the default value **5px** is used. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_GestureRecognizer*](capi-arkui-nativemodule-arkui-gesturerecognizer.md) | Returns the pointer to the created gesture. |

### createRotationGesture()

```c
ArkUI_GestureRecognizer* (*createRotationGesture)(int32_t fingersNum, double angleNum)
```

**Description**

Creates a rotation gesture.

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t fingersNum | Minimum number of fingers required to trigger the rotation gesture. The value ranges from 2 to 5. If the value is out of the range, the default value **2** is used. |
|  double angleNum | Minimum angle change required to trigger the rotation gesture, in degrees (deg). The default value is **1**. If this parameter is set to a value less than or equal to 0 or greater than 360, the default value **1** is used. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_GestureRecognizer*](capi-arkui-nativemodule-arkui-gesturerecognizer.md) | Returns the pointer to the created gesture. |

### createSwipeGesture()

```c
ArkUI_GestureRecognizer* (*createSwipeGesture)(int32_t fingersNum, ArkUI_GestureDirectionMask directions, double speedNum)
```

**Description**

Creates a swipe gesture.This API is used to implement a swipe gesture, which can be recognized when the swipe speed (px/s) is higher than that specified by **speedNum**.

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t fingersNum | Minimum number of fingers required to trigger the swipe gesture. The value ranges from 1 to 10. |
|  ArkUI_GestureDirectionMask directions | Directions in which the swipe gesture can be recognized. |
|  double speedNum | Minimum speed required to recognize the swipe gesture, in px/s. If this parameter is set to a value less than or equal to 0, the default value **100px/s** is used. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_GestureRecognizer*](capi-arkui-nativemodule-arkui-gesturerecognizer.md) | Returns the pointer to the created gesture. |

### createGroupGesture()

```c
ArkUI_GestureRecognizer* (*createGroupGesture)(ArkUI_GroupGestureMode gestureMode)
```

**Description**

Creates a gesture group.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_GroupGestureMode](capi-native-gesture-h.md#arkui_groupgesturemode) gestureMode | Gesture group mode. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_GestureRecognizer*](capi-arkui-nativemodule-arkui-gesturerecognizer.md) | Returns the pointer to the created gesture group. |

### dispose()

```c
void (*dispose)(ArkUI_GestureRecognizer* recognizer)
```

**Description**

Disposes of a gesture to release resources.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture to be disposed of. |

### addChildGesture()

```c
int32_t (*addChildGesture)(ArkUI_GestureRecognizer* group, ArkUI_GestureRecognizer* child)
```

**Description**

Adds a gesture to a gesture group.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* group | Pointer to the target gesture group. |
|  [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* child | Pointer to the target gesture. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Error code.          <br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>    <br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs, for example, attempting to          add a gesture to an object that is not a gesture group. |

### removeChildGesture()

```c
int32_t (*removeChildGesture)(ArkUI_GestureRecognizer* group, ArkUI_GestureRecognizer* child)
```

**Description**

Removes a gesture from a gesture group.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* group | Pointer to the target gesture group. |
|  [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* child | Pointer to the target gesture. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Error code.          <br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>    <br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### setGestureEventTarget()

```c
int32_t (*setGestureEventTarget)(ArkUI_GestureRecognizer* recognizer, ArkUI_GestureEventActionTypeMask actionTypeMask, void* extraParams,void (*targetReceiver)(ArkUI_GestureEvent* event, void* extraParams))
```

**Description**

Registers a callback for gestures.

**Parameters**:

| Parameter | Description |
| -- | -- |
| recognizer | Pointer to a gesture recognizer. |
| actionTypeMask | Gesture event types. Multiple callbacks can be registered at once, with the callback event types distinguished in the callbacks. Example: actionTypeMask = GESTURE_EVENT_ACTION_ACCEPT \| GESTURE_EVENT_ACTION_UPDATE; |
|  void* extraParams | Context passed in the **targetReceiver** callback. |
| targetReceiver | Callback to register for processing the gesture event types. **event** indicates the gesture callback data. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Error code.          <br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>    <br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### addGestureToNode()

```c
int32_t (*addGestureToNode)(ArkUI_NodeHandle node, ArkUI_GestureRecognizer* recognizer, ArkUI_GesturePriority mode, ArkUI_GestureMask mask)
```

**Description**

Adds a gesture to a UI component.

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | Pointer to the ArkUI component node to which you want to add the gesture. |
|  [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Gesture to be added to the UI component. |
|  [ArkUI_GesturePriority](capi-native-gesture-h.md#arkui_gesturepriority) mode | Mode of the gesture. |
|  [ArkUI_GestureMask](capi-native-gesture-h.md#arkui_gesturemask) mask | Gesture masking mode. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Error code.          <br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>    <br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### removeGestureFromNode()

```c
int32_t (*removeGestureFromNode)(ArkUI_NodeHandle node, ArkUI_GestureRecognizer* recognizer)
```

**Description**

Removes a gesture from a node.

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | Pointer to the node from which you want to remove the gesture. |
|  [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Gesture to be removed. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Error code.          <br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>    <br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### setGestureInterrupterToNode()

```c
int32_t (*setGestureInterrupterToNode)(ArkUI_NodeHandle node, ArkUI_GestureInterruptResult (*interrupter)(ArkUI_GestureInterruptInfo* info))
```

**Description**

Sets a gesture interruption callback for a node.

**Parameters**:

| Parameter | Description |
| -- | -- |
| node | Pointer to the ArkUI node for which you want to set a gesture interruption callback. |
| interrupter | Indicates the gesture interruption callback to set. <b>info</b> indicates the gesture interruption data. If <b>interrupter</b> returns <b>GESTURE_INTERRUPT_RESULT_CONTINUE</b>, the gesture recognition process continues. If it returns <b>GESTURE_INTERRUPT_RESULT_REJECT</b>, the gesture recognition process is paused. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Error code.          <br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>    <br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### getGestureType()

```c
ArkUI_GestureRecognizerType (*getGestureType)(ArkUI_GestureRecognizer* recognizer)
```

**Description**

Obtains the type of a gesture.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_GestureRecognizerType](capi-native-gesture-h.md#arkui_gesturerecognizertype) | Returns the gesture type. |

### setInnerGestureParallelTo()

```c
int32_t (*setInnerGestureParallelTo)(ArkUI_NodeHandle node, void* userData, ArkUI_GestureRecognizer* (*parallelInnerGesture)(ArkUI_ParallelInnerGestureEvent* event))
```

**Description**

Sets the callback function for the parallel internal gesture event.

**Parameters**:

| Parameter | Description |
| -- | -- |
| node | Pointer to the ArkUI node for which you want to set the callback of the parallel internal gesture event. |
| userData | Custom data. |
| parallelInnerGesture | Parallel internal gesture event. **event** returns the data of the parallel internal gesture event. **parallelInnerGesture** returns the pointer to the gesture recognizer that requires parallel recognition. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>    <br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### createTapGestureWithDistanceThreshold()

```c
ArkUI_GestureRecognizer* (*createTapGestureWithDistanceThreshold)(int32_t countNum, int32_t fingersNum, double distanceThreshold)
```

**Description**

Creates a tap gesture that is subject to distance restrictions.

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t countNum | Number of consecutive taps. If the value is less than 1 or is not set, the default value **1** is used. |
|  int32_t fingersNum | Number of fingers required to trigger the tap gesture. The value ranges from 1 to 10. If the value is less than 1 or is not set, the default value **1** is used. |
|  double distanceThreshold | Allowed moving distance of a finger. If the value is less than 0 or is not set, it will be converted to the default value of infinity. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_GestureRecognizer*](capi-arkui-nativemodule-arkui-gesturerecognizer.md) | Returns the pointer to the created gesture. |


