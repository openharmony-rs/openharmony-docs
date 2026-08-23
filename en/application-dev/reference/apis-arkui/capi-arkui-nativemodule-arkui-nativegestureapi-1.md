# ArkUI_NativeGestureAPI_1

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=a982f9d9be2aa48466f66955fc58f87c03f60f05 translatedAt=2026-08-20T07:25:35.052Z pushedAt=2026-08-21T04:13:42.648Z -->

```c
typedef struct {...} ArkUI_NativeGestureAPI_1
```

## Overview

Defines the APIs for creating tap, long press, pan, pinch, rotation, and fling gestures as well as gesture groups. This struct also supports binding gestures, removing gestures, and setting gesture interruption callbacks and parallel internal gesture callbacks, for configuring and managing touch interaction recognition and event processing of components.

When using this module to configure gestures, it is recommended to follow the process below: call APIs such as [createTapGesture](#createtapgesture) to create a gesture recognizer, call [setGestureEventTarget](#setgestureeventtarget) to register the gesture event callback, and then call [addGestureToNode](#addgesturetonode) to bind the gesture recognizer to a component node. When the gesture is no longer used, call [dispose](#dispose) to release the gesture resources. If you need to unbind the node first, call [removeGestureFromNode](#removegesturefromnode) before calling **dispose()**. For gesture competition scenarios, you can configure the response policy through the gesture priority, mask mode, or [setGestureInterrupterToNode](#setgestureinterruptertonode). For scenarios where internal gestures of a component and external custom gestures need to be recognized in parallel, call [setInnerGestureParallelTo](#setinnergestureparallelto) to set the parallel internal gesture event callback.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_gesture.h](capi-native-gesture-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| int32_t version | The struct version is 1. |

### Member Functions

| Name | Description |
| -- | -- |
| [ArkUI_GestureRecognizer* (\*createTapGesture)(int32_t countNum, int32_t fingersNum)](#createtapgesture) | Creates a tap gesture. The gesture recognizer returned after the gesture is created successfully can be added to a node through **addGestureToNode()**. When the gesture is no longer used, call **dispose()** to release the resources. After the release, the gesture recognizer must not be used again. If you need to unbind the node first, call **removeGestureFromNode()** before **dispose()**. 1. This API is used to trigger a tap gesture with one, two, or more taps. 2. When multi-tap is configured, the timeout between the last finger up of the previous tap and the first finger down of the next tap is 300 ms. 3. If the distance between the last tapped position and the current tapped position exceeds 60 vp, gesture recognition fails. 4. When multiple fingers are configured for a gesture, the recognition fails if the number of fingers touching the screen within 300 ms of the first finger's being pressed is less than the required count, or if the number of fingers lifted from the screen within 300 ms of the first finger's being lifted is less than the required count. 5. When the number of fingers touching the screen exceeds the set value, the gesture can be recognized. |
| [ArkUI_GestureRecognizer* (\*createLongPressGesture)(int32_t fingersNum, bool repeatResult, int32_t durationNum)](#createlongpressgesture) | Creates a long press gesture. The gesture recognizer returned after the gesture is created successfully can be added to a node through **addGestureToNode()**. When the gesture is no longer used, call **dispose()** to release the resources. After the release, the gesture recognizer must not be used again. If you need to unbind the node first, call **removeGestureFromNode()** before **dispose()**. 1. This API is used to trigger a long press gesture, which requires one or more fingers with a minimum 500 ms hold-down time. 2. In components that support drag actions by default, such as **Text**, **TextInput**, **TextArea**, **HyperLink**, **Image**, and **RichEditor**, the long press gesture may conflict with the drag action. If this occurs, the event priority is determined as follows: If the duration of the long press gesture is less than 500 ms, the long press gesture receives a higher response priority than the drag action. If the duration of the long press gesture is greater than or equal to 500 ms, the drag action receives a higher response priority than the long press gesture. 3. If a finger moves more than 15 px after being pressed, the gesture recognition fails. |
| [ArkUI_GestureRecognizer* (\*createPanGesture)(int32_t fingersNum, ArkUI_GestureDirectionMask directions, double distanceNum)](#createpangesture) | Creates a pan gesture. Different from [createSwipeGesture](#createswipegesture) (swipe gesture), the pan gesture is triggered based on the minimum drag distance, while the swipe gesture is triggered based on the minimum swipe speed. The gesture recognizer returned after the gesture is created successfully can be added to a node through **addGestureToNode()**. When the gesture is no longer used, call **dispose()** to release the resources. After the release, the gesture recognizer must not be used again. If you need to unbind the node first, call **removeGestureFromNode()** before **dispose()**. 1. This API is used to trigger a pan gesture when the movement distance of a finger on the screen exceeds the minimum value. 2. If a swipe on the **Tabs** component and this pan gesture event occur at the same time, set **distanceNum** to **1** to make dragging more sensitive and avoid response conflicts between the **Tabs** component swipe event and this pan gesture event. |
| [ArkUI_GestureRecognizer* (\*createPinchGesture)(int32_t fingersNum, double distanceNum)](#createpinchgesture) | Creates a pinch gesture. The gesture recognizer returned after the gesture is created successfully can be added to a node through **addGestureToNode()**. When the gesture is no longer used, call **dispose()** to release the resources. After the release, the gesture recognizer must not be used again. If you need to unbind the node first, call **removeGestureFromNode()** before **dispose()**. 1. This API is used to trigger a pinch gesture, which requires two to five fingers with a minimum pinch distance of pixels specified by **distanceNum**. 2. The number of fingers triggering the gesture can be greater than the value of **fingersNum**, but only the first fingers equal to the value of **fingersNum** participate in the gesture calculation. |
| [ArkUI_GestureRecognizer* (\*createRotationGesture)(int32_t fingersNum, double angleNum)](#createrotationgesture) | Creates a rotation gesture. The gesture recognizer returned after the gesture is created successfully can be added to a node through **addGestureToNode()**. When the gesture is no longer used, call **dispose()** to release the resources. After the release, the gesture recognizer must not be used again. If you need to unbind the node first, call **removeGestureFromNode()** before **dispose()**. 1. This API is used to trigger a rotation gesture, which requires two to five fingers with a minimum 1-degree rotation angle (specified by **angleNum**). 2. The number of fingers triggering the gesture can be greater than the value of **fingersNum**, but only the first two fingers that are pressed participate in the gesture calculation. |
| [ArkUI_GestureRecognizer* (\*createSwipeGesture)(int32_t fingersNum, ArkUI_GestureDirectionMask directions, double speedNum)](#createswipegesture) | Creates a swipe gesture. The gesture recognizer returned after the gesture is created successfully can be added to a node through **addGestureToNode()**. When the gesture is no longer used, call **dispose()** to release the resources. After the release, the gesture recognizer must not be used again. If you need to unbind the node first, call **removeGestureFromNode()** before **dispose()**. This API is used to implement a swipe gesture, which can be recognized when the swipe speed (px/s) is higher than that specified by **speedNum**. |
| [ArkUI_GestureRecognizer* (\*createGroupGesture)(ArkUI_GroupGestureMode gestureMode)](#creategroupgesture) | Creates a gesture group. After it is created successfully, call **addChildGesture()** to add child gestures to the gesture group, and then bind the gesture group to a node through **addGestureToNode()**. When a child gesture is no longer used, call **removeChildGesture()** as needed to remove the child gesture, and call **dispose()** to release the resources. After the release, the gesture group must not be used again. If you need to unbind the node first, call **removeGestureFromNode()** before **dispose()**. |
| [void (\*dispose)(ArkUI_GestureRecognizer* recognizer)](#dispose) | Disposes of the gesture created through **createTapGesture()**, **createLongPressGesture()**, **createPanGesture()**, **createPinchGesture()**, **createRotationGesture()**, **createSwipeGesture()**, **createGroupGesture()**, or **createTapGestureWithDistanceThreshold()** to release the resources. If the gesture has been added to a node through **addGestureToNode()**, it is recommended to call **removeGestureFromNode()** to unbind the node before calling **dispose()**. After **dispose()** is called, the gesture pointer must not be used again. |
| [int32_t (\*addChildGesture)(ArkUI_GestureRecognizer* group, ArkUI_GestureRecognizer* child)](#addchildgesture) | Adds a child gesture to the gesture group created through **createGroupGesture()**. You need to create the gesture group and the child gesture first, and then call **addChildGesture()** to establish the association. After the child gesture is added, it participates in the recognition process of the gesture group. When the child gesture no longer needs to participate in the gesture group recognition, call **removeChildGesture()** to remove the association. |
| [int32_t (\*removeChildGesture)(ArkUI_GestureRecognizer* group, ArkUI_GestureRecognizer* child)](#removechildgesture) | Removes the child gesture that has been added through **addChildGesture()** from the gesture group. After the call, the child gesture no longer participates in the gesture group recognition as a child gesture of the gesture group. |
| [int32_t (\*setGestureEventTarget)(ArkUI_GestureRecognizer* recognizer, ArkUI_GestureEventActionTypeMask actionTypeMask, void* extraParams,void (\*targetReceiver)(ArkUI_GestureEvent* event, void* extraParams))](#setgestureeventtarget) | Sets the gesture association callback, for scenarios where you need to listen for events such as gesture triggering, updating, or ending and perform business processing. You need to create a gesture recognizer through APIs such as **createTapGesture()** and **createLongPressGesture()** first, call **setGestureEventTarget()** to set the event callback, and bind the gesture to a node through **addGestureToNode()**. It is recommended to call **setGestureEventTarget()** before **addGestureToNode()** to ensure that the gesture can respond to events immediately after being bound to the node. |
| [int32_t (\*addGestureToNode)(ArkUI_NodeHandle node, ArkUI_GestureRecognizer* recognizer, ArkUI_GesturePriority mode, ArkUI_GestureMask mask)](#addgesturetonode) | Adds the gesture created through APIs such as **createTapGesture()** and **createLongPressGesture()** to a UI component. You should create a gesture recognizer first, and then call **addGestureToNode()** to bind the gesture to the node. When the node no longer needs to respond to the gesture, call **removeGestureFromNode()** to unbind it, and call **dispose()** when releasing resources. |
| [int32_t (\*removeGestureFromNode)(ArkUI_NodeHandle node, ArkUI_GestureRecognizer* recognizer)](#removegesturefromnode) | Removes the gesture that has been added through **addGestureToNode()** from the node. After the call, the node no longer responds to the gesture. If you need to release the gesture resources, it is recommended to call **removeGestureFromNode()** to unbind the node first, and then call **dispose()**. |
| [int32_t (\*setGestureInterrupterToNode)(ArkUI_NodeHandle node, ArkUI_GestureInterruptResult (\*interrupter)(ArkUI_GestureInterruptInfo* info))](#setgestureinterruptertonode) | Sets the node gesture interruption callback, for scenarios where you need to determine whether the gesture continues to be recognized based on service conditions, such as handling gesture conflicts between parent and child nodes or dynamically controlling gesture responses. This callback applies to gestures added to the node through **addGestureToNode()** and built-in gestures of the component. It is triggered during gesture recognition, and you can determine whether the gesture continues to be recognized or is interrupted through the callback result. |
| [ArkUI_GestureRecognizerType (\*getGestureType)(ArkUI_GestureRecognizer* recognizer)](#getgesturetype) | Obtains the gesture type of the gesture recognizer, which can be used to determine whether the current gesture belongs to a specific category such as tap, long press, pan, pinch, rotation, or swipe. |
| [int32_t (\*setInnerGestureParallelTo)(ArkUI_NodeHandle node, void* userData, ArkUI_GestureRecognizer* (\*parallelInnerGesture)(ArkUI_ParallelInnerGestureEvent* event))](#setinnergestureparallelto) | Sets the parallel inner gesture event callback, for scenarios where internal gestures of a component and external custom gestures need to be recognized in parallel. You need to create a custom gesture recognizer through APIs such as **createPanGesture()** first, bind the gesture to the node through **addGestureToNode()**, and call **setInnerGestureParallelTo()** to set the parallel inner gesture event callback. The gesture recognizer returned by the callback function **parallelInnerGesture** should be a custom gesture recognizer created through the **create** series APIs, used for parallel recognition with the inner gestures of the component.<br>**Note:** This callback is triggered only when the gestures bound to the node include a pan gesture (created by **createPanGesture**). If the node has no pan gesture bound, this callback is not triggered. |
| [ArkUI_GestureRecognizer* (\*createTapGestureWithDistanceThreshold)(int32_t countNum, int32_t fingersNum, double distanceThreshold)](#createtapgesturewithdistancethreshold) | Creates a tap gesture with a movement range limit. The gesture recognizer returned after the gesture is created successfully can be added to a node through **addGestureToNode()**. When the gesture is no longer used, call **dispose()** to release the resources. After the release, the gesture recognizer must not be used again. If you need to unbind the node first, call **removeGestureFromNode()** before **dispose()**. 1. This API is used to trigger a tap gesture with one, two, or more taps. 2. If multi-tap is configured, the timeout between the last finger up of the previous tap and the first finger down of the next tap is 300 ms. 3. If the distance between the last tapped position and the current tapped position exceeds 60 vp, gesture recognition fails. 4. When multiple fingers are configured for a gesture, the recognition fails if the number of fingers touching the screen within 300 ms of the first finger's being pressed is less than the required count, or if the number of fingers lifted from the screen within 300 ms of the first finger's being lifted is less than the required count. 5. When the number of fingers touching the screen exceeds the set value, the gesture can be recognized. 6. If the finger moves beyond the preset distance limit, gesture recognition fails. |

## Member Function Description

### createTapGesture()

```c
ArkUI_GestureRecognizer* (*createTapGesture)(int32_t countNum, int32_t fingersNum)
```

**Description**

Creates a tap gesture. The gesture recognizer returned after the gesture is created successfully can be added to a node through **addGestureToNode()**. When the gesture is no longer used, call **dispose()** to release the resources. After the release, the gesture recognizer must not be used again. If you need to unbind the node first, call **removeGestureFromNode()** before **dispose()**.

1. This API is used to trigger a tap gesture with one, two, or more taps.

2. When multi-tap is configured, the timeout between the last finger up of the previous tap and the first finger down of the next tap is 300 ms.

3. If the distance between the last tapped position and the current tapped position exceeds 60 vp, gesture recognition fails.

4. When multiple fingers are configured for a gesture, the recognition fails if the number of fingers touching the screen within 300 ms of the first finger's being pressed is less than the required count, or if the number of fingers lifted from the screen within 300 ms of the first finger's being lifted is less than the required count.

5. When the number of fingers touching the screen exceeds the set value, the gesture can be recognized.

**Parameters**

| Name | Description |
| -- | -- |
| int32_t countNum | Number of consecutive taps to recognize. The value is an integer greater than 0. If the value is less than 1, the default value **1** is used. |
| int32_t fingersNum | Number of fingers that trigger the tap. The minimum value is 1 and the maximum value is 10. If the value is less than 1, the minimum value **1** is used. If the value is greater than 10, the maximum value **10** is used. |

**Returns**

| Type | Description |
|------------------------------| -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* | Pointer to the created tap gesture recognizer, which can be used to bind a node, register a callback, or manage tap gesture recognition. |

### createLongPressGesture()

```c
ArkUI_GestureRecognizer* (*createLongPressGesture)(int32_t fingersNum, bool repeatResult, int32_t durationNum)
```

**Description**

Creates a long press gesture. The gesture recognizer returned after the gesture is created successfully can be added to a node through **addGestureToNode()**. When the gesture is no longer used, call **dispose()** to release the resources. After the release, the gesture recognizer must not be used again. If you need to unbind the node first, call **removeGestureFromNode()** before **dispose()**.

1. This API is used to trigger a long press gesture, which requires one or more fingers with a minimum 500 ms hold-down time.

2. In components that support drag actions by default, such as **Text**, **TextInput**, **TextArea**, **HyperLink**, **Image**, and **RichEditor**, the long press gesture may conflict with the drag action.

   If this occurs, the event priority is determined as follows: 

   If the duration of the long press gesture is less than 500 ms, the long press gesture receives a higher response priority than the drag action.

   If the duration of the long press gesture is greater than or equal to 500 ms, the drag action receives a higher response priority than the long press gesture.

3. If a finger moves more than 15 px after being pressed, the gesture recognition fails.

**Parameters**

| Name | Description |
| -- | -- |
| int32_t fingersNum | Minimum number of fingers that triggers the long press. The value ranges from 1 to 10. If the value is out of range, the default value **1** is used. |
|  bool repeatResult | Whether to trigger the event callback continuously.<br>**true**: triggers continuously; **false**: does not trigger continuously. |
|  int32_t durationNum | Minimum duration that triggers the long press, in milliseconds (ms). The valid value is greater than 0. If the value is less than or equal to 0, the default value 500 ms is used. When the component supports dragging by default, if the long press trigger time is less than 500 ms, the long press event takes precedence over the drag event; if the long press trigger time is greater than or equal to 500 ms, the drag event takes precedence over the long press event. |

**Returns**

| Type | Description |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* | Pointer to the created long press gesture recognizer, which can be used to bind a node, register a callback, or manage long press gesture recognition. |

### createPanGesture()

```c
ArkUI_GestureRecognizer* (*createPanGesture)(int32_t fingersNum, ArkUI_GestureDirectionMask directions, double distanceNum)
```

**Description**

Creates a pan gesture. Different from [createSwipeGesture](#createswipegesture) (swipe gesture), the pan gesture is triggered based on the minimum drag distance, while the swipe gesture is triggered based on the minimum swipe speed. The gesture recognizer returned after the gesture is created successfully can be added to a node through **addGestureToNode()**. When the gesture is no longer used, call **dispose()** to release the resources. After the release, the gesture recognizer must not be used again. If you need to unbind the node first, call **removeGestureFromNode()** before **dispose()**.

1. This API is used to trigger a pan gesture when the movement distance of a finger on the screen exceeds the minimum value.

2. If a swipe on the **Tabs** component and this pan gesture event occur at the same time, set **distanceNum** to **1** to make dragging more sensitive and avoid response conflicts between the **Tabs** component swipe event and this pan gesture event.

**Parameters**

| Name                                                                  | Description |
|----------------------------------------------------------------------| -- |
| int32_t fingersNum                                                   | Minimum number of fingers that trigger the pan gesture. The value ranges from 1 to 10. If the value is out of range, the default value **1** is used. |
| [ArkUI_GestureDirectionMask](capi-native-gesture-h.md#variables) directions | Gesture direction that triggers the pan gesture. This enumerated value supports the logical AND (&) and logical OR (\|) operations. You can select the direction based on your service requirements: **GESTURE_DIRECTION_HORIZONTAL** applies to scenarios where only horizontal panning is recognized, **GESTURE_DIRECTION_VERTICAL** applies to scenarios where only vertical panning is recognized, **GESTURE_DIRECTION_LEFT/RIGHT/UP/DOWN** applies to scenarios where only a single panning direction is recognized, **GESTURE_DIRECTION_ALL** applies to scenarios where the gesture is triggered in any direction, and **GESTURE_DIRECTION_NONE** indicates that the gesture event is not triggered in any direction. |
| double distanceNum | Minimum pan distance that triggers the pan gesture event, in px. The value range is (0, +∞). If the value is less than or equal to 0, the default value **5px** is used. |

**Returns**

| Type | Description |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* | Pointer to the created pan gesture recognizer, which can be used to bind a node, register a callback, or manage pan gesture recognition. |

### createPinchGesture()

```c
ArkUI_GestureRecognizer* (*createPinchGesture)(int32_t fingersNum, double distanceNum)
```

**Description**

Creates a pinch gesture. The gesture recognizer returned after the gesture is created successfully can be added to a node through **addGestureToNode()**. When the gesture is no longer used, call **dispose()** to release the resources. After the release, the gesture recognizer must not be used again. If you need to unbind the node first, call **removeGestureFromNode()** before **dispose()**.

1. This API is used to trigger a pinch gesture, which requires two to five fingers with a minimum pinch distance of pixels specified by **distanceNum**.

2. The number of fingers triggering the gesture can be greater than the value of **fingersNum**, but only the first fingers equal to the value of **fingersNum** participate in the gesture calculation.

**Parameters**

| Name | Description |
| -- | -- |
| int32_t fingersNum | Minimum number of fingers required to trigger a pinch gesture. The value ranges from 2 to 5. If the value is out of range, the default value **2** is used. |
| double distanceNum | Minimum recognition distance, in px. The value range is (0, +∞). If the value is less than or equal to 0, the default value **5px** is used. |

**Returns**

| Type | Description |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* | Pointer to the created pinch gesture recognizer, which can be used to bind a node, register a callback, or manage pinch gesture recognition. |

### createRotationGesture()

```c
ArkUI_GestureRecognizer* (*createRotationGesture)(int32_t fingersNum, double angleNum)
```

**Description**

Creates a rotation gesture. The gesture recognizer returned after the gesture is created successfully can be added to a node through **addGestureToNode()**. When the gesture is no longer used, call **dispose()** to release the resources. After the release, the gesture recognizer must not be used again. If you need to unbind the node first, call **removeGestureFromNode()** before **dispose()**.

1. This API is used to trigger a rotation gesture, which requires two to five fingers with a minimum 1-degree rotation angle (specified by **angleNum**).

2. The number of fingers triggering the gesture can be greater than the value of **fingersNum**, but only the first two fingers that are pressed participate in the gesture calculation.

**Parameters**

| Name | Description |
| -- | -- |
| int32_t fingersNum | Minimum number of fingers required to trigger rotation. The value ranges from 2 to 5. If the value is out of range, the default value **2** is used. |
| double angleNum | Minimum angle change required to trigger the rotation gesture. The value ranges from (0, 360], in deg. Default value: **1deg**. If the value passed is less than or equal to 0 or greater than 360, it is converted to the default value **1**. |

**Returns**

| Type | Description |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* | Pointer to the created rotation gesture recognizer, which can be used to bind a node, register a callback, or manage rotation gesture recognition. |

### createSwipeGesture()

```c
ArkUI_GestureRecognizer* (*createSwipeGesture)(int32_t fingersNum, ArkUI_GestureDirectionMask directions, double speedNum)
```

**Description**

Creates a swipe gesture. The gesture recognizer returned after the gesture is created successfully can be added to a node through **addGestureToNode()**. When the gesture is no longer used, call **dispose()** to release the resources. After the release, the gesture recognizer must not be used again. If you need to unbind the node first, call **removeGestureFromNode()** before **dispose()**.

This API is used to implement a swipe gesture, which can be recognized when the swipe speed (px/s) is higher than that specified by **speedNum**.

**Parameters**

| Name | Description |
| -- | -- |
| int32_t fingersNum | Minimum number of fingers required to trigger the swipe. The value ranges from 1 to 10. If the value is out of range, the default value **1** is used. |
|  [ArkUI_GestureDirectionMask](capi-native-gesture-h.md#variables) directions | Swipe direction that triggers the swipe gesture. Select the direction based on the swipe direction to be recognized: **GESTURE_DIRECTION_HORIZONTAL** applies to horizontal swipe scenarios, **GESTURE_DIRECTION_VERTICAL** applies to vertical swipe scenarios, **GESTURE_DIRECTION_LEFT/RIGHT/UP/DOWN** applies to scenarios where only a single specified swipe direction is recognized, **GESTURE_DIRECTION_ALL** applies to scenarios where a swipe in any direction can be triggered, and **GESTURE_DIRECTION_NONE** indicates that no gesture event is triggered in any direction. |
|  double speedNum | Minimum speed for recognizing the swipe, in px/s. The value range is (0, +∞). If the value is less than or equal to 0, the default value **100px/s** is used. |

**Returns**

| Type | Description |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* | Pointer to the created swipe gesture recognizer, which can be used to bind a node, register a callback, or manage swipe gesture recognition. |

### createGroupGesture()

```cc
ArkUI_GestureRecognizer* (*createGroupGesture)(ArkUI_GroupGestureMode gestureMode)
```

**Description**

Creates a gesture group. After it is created successfully, call **addChildGesture()** to add child gestures to the gesture group, and then bind the gesture group to a node through **addGestureToNode()**. When a child gesture is no longer used, call **removeChildGesture()** as needed to remove the child gesture, and call **dispose()** to release the resources. After the release, the gesture group must not be used again. If you need to unbind the node first, call **removeGestureFromNode()** before **dispose()**.

**Parameters**

| Name                                                                                   | Description |
|---------------------------------------------------------------------------------------| -- |
| [ArkUI_GroupGestureMode](capi-native-gesture-h.md#arkui_groupgesturemode) gestureMode | Gesture group mode. **SEQUENTIAL_GROUP** applies to scenarios where multiple gestures need to be recognized in registration order. **PARALLEL_GROUP** applies to scenarios where multiple gestures need to be recognized simultaneously without affecting each other. **EXCLUSIVE_GROUP** applies to mutually exclusive scenarios where multiple gestures compete at the same time and the recognition of the others ends once any gesture is recognized successfully. |

**Returns**

| Type | Description |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* | Pointer to the created gesture group, which can be used to add, remove, or manage child gestures in group. |

### dispose()

```c
void (*dispose)(ArkUI_GestureRecognizer* recognizer)
```

**Description**

Disposes of the gesture created through **createTapGesture()**, **createLongPressGesture()**, **createPanGesture()**, **createPinchGesture()**, **createRotationGesture()**, **createSwipeGesture()**, **createGroupGesture()**, or **createTapGestureWithDistanceThreshold()** to release the resources. If the gesture has been added to a node through **addGestureToNode()**, it is recommended to call **removeGestureFromNode()** to unbind the node before calling **dispose()**. After **dispose()** is called, the gesture pointer must not be used again.

**Parameters**

| Name                                                                                   | Description |
|---------------------------------------------------------------------------------------| -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer| Pointer to the gesture to be disposed of. |

### addChildGesture()

```c
int32_t (*addChildGesture)(ArkUI_GestureRecognizer* group, ArkUI_GestureRecognizer* child)
```

**Description**

Adds a child gesture to the gesture group created through **createGroupGesture()**. You need to create the gesture group and the child gesture first, and then call **addChildGesture()** to establish the association. After the child gesture is added, it participates in the recognition process of the gesture group. When the child gesture no longer needs to participate in the gesture group recognition, call **removeChildGesture()** to remove the association.

**Parameters**

| Name | Description |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* group | Pointer to the gesture group to which the child gesture is to be added. |
|  [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* child | Pointer to the child gesture recognizer to be added to the gesture group. |

**Returns**

| Type | Description |
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs, for example, adding a gesture to a non-gesture-group object. |

### removeChildGesture()

```c
int32_t (*removeChildGesture)(ArkUI_GestureRecognizer* group, ArkUI_GestureRecognizer* child)
```

**Description**

Removes the child gesture that has been added through **addChildGesture()** from the gesture group. After the call, the child gesture no longer participates in the gesture group recognition as a child gesture of the gesture group.

**Parameters**

| Name | Description |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* group | Pointer to the gesture group from which the child gesture is to be removed. |
|  [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* child | Pointer to the child gesture recognizer to be removed from the gesture group. |

**Returns**

| Type | Description |
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### setGestureEventTarget()

```c
int32_t (*setGestureEventTarget)(ArkUI_GestureRecognizer* recognizer, ArkUI_GestureEventActionTypeMask actionTypeMask, void* extraParams,void (*targetReceiver)(ArkUI_GestureEvent* event, void* extraParams))
```

**Description**

Sets the gesture association callback, for scenarios where you need to listen for events such as gesture triggering, updating, or ending and perform business processing. You need to create a gesture recognizer through APIs such as **createTapGesture()** and **createLongPressGesture()** first, call **setGestureEventTarget()** to set the event callback, and bind the gesture to a node through **addGestureToNode()**. It is recommended to call **setGestureEventTarget()** before **addGestureToNode()** to ensure that the gesture can respond to events immediately after being bound to the node.

**Parameters**

| Name | Description |
|-------------------------------------------------------------------------------------------| -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer to which the callback event is bound. |
| [ArkUI_GestureEventActionTypeMask](capi-native-gesture-h.md#variables) actionTypeMask | Set of gesture event types to respond to. Multiple event types can be registered at a time, and the callback event type is distinguished in the callback. Example: **actionTypeMask = GESTURE_EVENT_ACTION_ACCEPT \| GESTURE_EVENT_ACTION_UPDATE;** |
| void* extraParams | Pointer to the context data passed when **targetReceiver** is called. Pass the corresponding data pointer when custom service data needs to be accessed in the callback. |
| targetReceiver | Gesture event callback function, with the signature **void (\*targetReceiver)(ArkUI_GestureEvent* event, void* extraParams)**, used to process events of the registered gesture types. Here, **event** indicates the gesture callback data, and **extraParams** indicates the context data passed during registration. No value is returned. |

**Returns**

| Type | Description |
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### addGestureToNode()

```c
int32_t (*addGestureToNode)(ArkUI_NodeHandle node, ArkUI_GestureRecognizer* recognizer, ArkUI_GesturePriority mode, ArkUI_GestureMask mask)
```

**Description**

Adds the gesture created through APIs such as **createTapGesture()** and **createLongPressGesture()** to a UI component. You should create a gesture recognizer first, and then call **addGestureToNode()** to bind the gesture to the node. When the node no longer needs to respond to the gesture, call **removeGestureFromNode()** to unbind it, and call **dispose()** when releasing resources.

**Parameters**

| Name                                                                                       | Description |
|-------------------------------------------------------------------------------------------| -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node                          | Pointer to the ArkUI component node to which the gesture is to be bound. |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer to be bound to this node. |
| [ArkUI_GesturePriority](capi-native-gesture-h.md#arkui_gesturepriority) mode | Gesture priority mode, which is used to set the response priority of the gesture after it is added to the node and its competition relationship with other gestures. |
| [ArkUI_GestureMask](capi-native-gesture-h.md#arkui_gesturemask) mask | Gesture mask mode, which is used to control the masking or pass-through relationship between the gesture and other gestures after it is added to the node. |

**Returns**

| Type | Description |
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### removeGestureFromNode()

```c
int32_t (*removeGestureFromNode)(ArkUI_NodeHandle node, ArkUI_GestureRecognizer* recognizer)
```

**Description**

Removes the gesture that has been added through **addGestureToNode()** from the node. After the call, the node no longer responds to the gesture. If you need to release the gesture resources, it is recommended to call **removeGestureFromNode()** to unbind the node first, and then call **dispose()**.

**Parameters**

| Name | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Pointer to the node from which the gesture is to be removed. |
|  [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer to be removed. |

**Returns**

| Type | Description |
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### setGestureInterrupterToNode()

```c
int32_t (*setGestureInterrupterToNode)(ArkUI_NodeHandle node, ArkUI_GestureInterruptResult (*interrupter)(ArkUI_GestureInterruptInfo* info))
```

**Description**

Sets the node gesture interruption callback, for scenarios where you need to determine whether the gesture continues to be recognized based on service conditions, such as handling gesture conflicts between parent and child nodes or dynamically controlling gesture responses. This callback applies to gestures added to the node through **addGestureToNode()** and built-in gestures of the component. It is triggered during gesture recognition, and you can determine whether the gesture continues to be recognized or is interrupted through the callback result.

**Parameters**

| Name                                                              | Description |
|------------------------------------------------------------------| -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Pointer to the ArkUI node for which the gesture interruption callback is to be set. |
| [ArkUI_GestureInterruptResult](capi-native-gesture-h.md#arkui_gestureinterruptresult) (\*interrupter)([ArkUI_GestureInterruptInfo](capi-arkui-nativemodule-arkui-gestureinterruptinfo.md)* info)     | Pointer to the interruption callback. **info** returns the gesture interruption data. If **interrupter** returns **GESTURE_INTERRUPT_RESULT_CONTINUE**, the gesture recognition process continues. If it returns **GESTURE_INTERRUPT_RESULT_REJECT**, the gesture recognition process is paused. If this parameter is set to a null pointer, the callback function is unregistered.<br>**Note:** After the event interruption callback is registered, it will be available in subsequent single-gesture processing. That is, even if you use the **setGestureInterrupterToNode** API to reset the gesture interruption callback to **nullptr** or use the [dispose](#dispose) API to dispose of the gesture that is about to be triggered, the callback will still respond when the trigger condition is met. If the object used in this callback has been released before the callback is triggered, ensure that the object is still valid when the callback is triggered, for example, by checking whether the object has been released before use, or by extending the object's lifecycle until after the callback is triggered. |

**Returns**

| Type | Description |
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### getGestureType()

```c
ArkUI_GestureRecognizerType (*getGestureType)(ArkUI_GestureRecognizer* recognizer)
```

**Description**

Obtains the gesture type.

**Parameters**

| Name | Description |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer. |

**Returns**

| Type                                                                                  | Description |
|-------------------------------------------------------------------------------------| -- |
| [ArkUI_GestureRecognizerType](capi-native-gesture-h.md#arkui_gesturerecognizertype) | Gesture type of the gesture recognizer. |

### setInnerGestureParallelTo()

```c
int32_t (*setInnerGestureParallelTo)(ArkUI_NodeHandle node, void* userData, ArkUI_GestureRecognizer* (*parallelInnerGesture)(ArkUI_ParallelInnerGestureEvent* event))
```

**Description**

Sets the parallel inner gesture event callback, for scenarios where internal gestures of a component and external custom gestures need to be recognized in parallel. You need to create a custom gesture recognizer through APIs such as **createPanGesture()** first, bind the gesture to the node through **addGestureToNode()**, and call **setInnerGestureParallelTo()** to set the parallel inner gesture event callback. The gesture recognizer returned by the callback function **parallelInnerGesture** should be a custom gesture recognizer created through the **create** series APIs, used for parallel recognition with the inner gestures of the component.

> **NOTE**
> This callback is triggered only when the gestures bound to the node include a pan gesture (created by **createPanGesture**). If the node has no pan gesture bound, this callback is not triggered.

**Parameters**

| Name                                                              | Description |
|------------------------------------------------------------------| -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Pointer to the ArkUI node for which the parallel inner gesture event callback is to be set. |
| void* userData | Pointer to the user-defined data, which is passed through as the context data of the parallel inner gesture event callback after being set, for you to use when processing the callback. Pass **nullptr** when no additional context needs to be passed. |
| parallelInnerGesture                                             | Parallel inner gesture event callback, with the signature ArkUI_GestureRecognizer* (\*parallelInnerGesture)(ArkUI_ParallelInnerGestureEvent* event), used to return the pointer to the gesture recognizer that needs to be recognized in parallel with the inner gesture based on the parallel inner gesture event data. Here, **event** indicates the parallel inner gesture event data, and the return value is the pointer to the gesture recognizer that needs to be recognized in parallel. |

**Returns**

| Type | Description |
| -- | -- |
| int32_t | Result code.<br>Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>            Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### createTapGestureWithDistanceThreshold()

```c
ArkUI_GestureRecognizer* (*createTapGestureWithDistanceThreshold)(int32_t countNum, int32_t fingersNum, double distanceThreshold)
```

**Description**

Creates a tap gesture with a movement range limit. The gesture recognizer returned after the gesture is created successfully can be added to a node through **addGestureToNode()**. When the gesture is no longer used, call **dispose()** to release the resources. After the release, the gesture recognizer must not be used again. If you need to unbind the node first, call **removeGestureFromNode()** before **dispose()**. 

1. This API is used to trigger a tap gesture with one, two, or more taps.

2. If multi-tap is configured, the timeout between the last finger up of the previous tap and the first finger down of the next tap is 300 ms.

3. If the distance between the last tapped position and the current tapped position exceeds 60 vp, gesture recognition fails.

4. When multiple fingers are configured for a gesture, the recognition fails if the number of fingers touching the screen within 300 ms of the first finger's being pressed is less than the required count, or if the number of fingers lifted from the screen within 300 ms of the first finger's being lifted is less than the required count.

5. When the number of fingers touching the screen exceeds the set value, the gesture can be recognized.

6. If the finger moves beyond the preset distance limit, gesture recognition fails.

**Parameters**

| Name | Description |
| -- | -- |
| int32_t countNum | Number of consecutive taps to recognize. The value is a positive integer. If the value is set to less than 1, it is converted to the default value **1**. |
|  int32_t fingersNum | Number of fingers that trigger the tap. The minimum is 1 and the maximum is 10. If the value is set to less than 1, it is processed as the minimum value **1**. If the value is set to greater than 10, it is processed as the maximum value **10**. |
|  double distanceThreshold | Allowed movement distance range of the fingers, in vp. The value range is (0, +∞). If the value is set to less than or equal to 0, it is converted to the default value (infinity). |

**Returns**

| Type | Description |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* | Pointer to the created tap gesture recognizer with a movement range limit. It can be used to bind a node, register a callback, or manage tap gesture recognition. |