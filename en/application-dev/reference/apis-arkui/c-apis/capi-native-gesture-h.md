# native_gesture.h

## Overview

Declares the APIs of **NativeGesture**.

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_NativeGestureAPI_1](capi-arkui-nativemodule-arkui-nativegestureapi-1.md) | ArkUI_NativeGestureAPI_1 | Defines the gesture APIs. |
| [ArkUI_NativeGestureAPI_2](capi-arkui-nativemodule-arkui-nativegestureapi-2.md) | ArkUI_NativeGestureAPI_2 | Defines a collection of gesture APIs. |
| [ArkUI_NativeGestureAPI_3](capi-arkui-nativemodule-arkui-nativegestureapi-3.md) | ArkUI_NativeGestureAPI_3 | Defines a collection of gesture APIs, including gesture APIs in the {@link ArkUI_NativeGestureAPI_1} and<br>{@link ArkUI_NativeGestureAPI_2} structs and new gesture APIs. |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md) | ArkUI_GestureRecognizer | Defines a gesture recognizer. |
| [ArkUI_GestureInterruptInfo](capi-arkui-nativemodule-arkui-gestureinterruptinfo.md) | ArkUI_GestureInterruptInfo | Defines gesture interruption information. |
| [ArkUI_GestureEvent](capi-arkui-nativemodule-arkui-gestureevent.md) | ArkUI_GestureEvent | Defines a gesture event. |
| [ArkUI_GestureEventTargetInfo](capi-arkui-nativemodule-arkui-gestureeventtargetinfo.md) | ArkUI_GestureEventTargetInfo | Defines gesture event target information. |
| [ArkUI_ParallelInnerGestureEvent](capi-arkui-nativemodule-arkui-parallelinnergestureevent.md) | ArkUI_ParallelInnerGestureEvent | Defines a parallel internal gesture event. |
| [ArkUI_ParallelGestureEvent](capi-arkui-nativemodule-arkui-parallelgestureevent.md) | ArkUI_ParallelGestureEvent | Defines a parallel gesture event. This struct is used by the callback function {@link setGestureParallelTo} for the parallel gesture event. |
| [ArkUI_TouchRecognizer](capi-arkui-nativemodule-arkui-touchrecognizer.md) | ArkUI_TouchRecognizer | Defines a touch recognizer. |
| [ArkUI_GestureRecognizer*](capi-arkui-nativemodule-arkui-gesturerecognizer8h.md) | ArkUI_GestureRecognizerHandle | Defines the gesture recognizer handle. |
| [ArkUI_TouchRecognizer*](capi-arkui-nativemodule-arkui-touchrecognizer8h.md) | ArkUI_TouchRecognizerHandle | Defines a touch recognizer handle. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_GestureEventActionType](#arkui_gestureeventactiontype) | ArkUI_GestureEventActionType | Enumerates gesture event types. |
| [ArkUI_GesturePriority](#arkui_gesturepriority) | ArkUI_GesturePriority | Enumerates gesture event modes. |
| [ArkUI_GroupGestureMode](#arkui_groupgesturemode) | ArkUI_GroupGestureMode | Enumerates gesture group modes. |
| [ArkUI_GestureDirection](#arkui_gesturedirection) | ArkUI_GestureDirection | Enumerates gesture directions. |
| [ArkUI_GestureMask](#arkui_gesturemask) | ArkUI_GestureMask | Enumerates gesture masking modes. |
| [ArkUI_GestureRecognizerType](#arkui_gesturerecognizertype) | ArkUI_GestureRecognizerType | Enumerates gesture recognizer types. |
| [ArkUI_GestureInterruptResult](#arkui_gestureinterruptresult) | ArkUI_GestureInterruptResult | Enumerates gesture interruption results. |
| [ArkUI_GestureRecognizerState](#arkui_gesturerecognizerstate) | ArkUI_GestureRecognizerState | Enumerates the gesture recognizer states. |
| [OH_ArkUI_GestureCollectIntervention](#oh_arkui_gesturecollectintervention) | OH_ArkUI_GestureCollectIntervention | Defines the intervention types for gesture and event collection. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*ArkUI_GestureRecognizerDisposeNotifyCallback)(ArkUI_GestureRecognizer* recognizer, void* userData)](#arkui_gesturerecognizerdisposenotifycallback) | ArkUI_GestureRecognizerDisposeNotifyCallback | Defines a callback function for notifying gesture recognizer destruction. |
| [bool OH_ArkUI_GestureInterruptInfo_GetSystemFlag(const ArkUI_GestureInterruptInfo* event)](#oh_arkui_gestureinterruptinfo_getsystemflag) | - | Checks whether a gesture is a built-in gesture of the component. |
| [ArkUI_GestureRecognizer* OH_ArkUI_GestureInterruptInfo_GetRecognizer(const ArkUI_GestureInterruptInfo* event)](#oh_arkui_gestureinterruptinfo_getrecognizer) | - | Obtains the pointer to the interrupted gesture recognizer. |
| [ArkUI_GestureEvent* OH_ArkUI_GestureInterruptInfo_GetGestureEvent(const ArkUI_GestureInterruptInfo* event)](#oh_arkui_gestureinterruptinfo_getgestureevent) | - | Obtains the pointer to the interrupted gesture event. |
| [int32_t OH_ArkUI_GestureInterruptInfo_GetSystemRecognizerType(const ArkUI_GestureInterruptInfo* event)](#oh_arkui_gestureinterruptinfo_getsystemrecognizertype) | - | Obtains the type of the system built-in gesture to trigger. |
| [int32_t OH_ArkUI_GestureInterruptInfo_GetTouchRecognizers(const ArkUI_GestureInterruptInfo* info, ArkUI_TouchRecognizerHandleArray* recognizers, int32_t* size)](#oh_arkui_gestureinterruptinfo_gettouchrecognizers) | - | Obtains touch recognizers from gesture interruption information. |
| [ArkUI_NodeHandle OH_ArkUI_TouchRecognizer_GetNodeHandle(const ArkUI_TouchRecognizerHandle recognizer)](#oh_arkui_touchrecognizer_getnodehandle) | - | Obtains the component handle corresponding to a touch recognizer. |
| [int32_t OH_ArkUI_TouchRecognizer_CancelTouch(ArkUI_TouchRecognizerHandle recognizer, ArkUI_GestureInterruptInfo* info)](#oh_arkui_touchrecognizer_canceltouch) | - | Sends a cancel touch event to a touch recognizer in a gesture interruption callback. |
| [ArkUI_GestureEventActionType OH_ArkUI_GestureEvent_GetActionType(const ArkUI_GestureEvent* event)](#oh_arkui_gestureevent_getactiontype) | - | Obtains the gesture event type. |
| [const ArkUI_UIInputEvent* OH_ArkUI_GestureEvent_GetRawInputEvent(const ArkUI_GestureEvent* event)](#oh_arkui_gestureevent_getrawinputevent) | - | Obtains gesture input. |
| [int32_t OH_ArkUI_LongPress_GetRepeatCount(const ArkUI_GestureEvent* event)](#oh_arkui_longpress_getrepeatcount) | - | Checks whether the event is a repeated trigger event. |
| [float OH_ArkUI_PanGesture_GetVelocity(const ArkUI_GestureEvent* event)](#oh_arkui_pangesture_getvelocity) | - | Obtains the velocity of a pan gesture along the main axis. |
| [float OH_ArkUI_PanGesture_GetVelocityX(const ArkUI_GestureEvent* event)](#oh_arkui_pangesture_getvelocityx) | - | Obtains the velocity of a pan gesture along the x-axis. |
| [float OH_ArkUI_PanGesture_GetVelocityY(const ArkUI_GestureEvent* event)](#oh_arkui_pangesture_getvelocityy) | - | Obtains the velocity of a pan gesture along the y-axis. |
| [float OH_ArkUI_PanGesture_GetOffsetX(const ArkUI_GestureEvent* event)](#oh_arkui_pangesture_getoffsetx) | - | Obtains the relative offset of a pan gesture along the x-axis. |
| [float OH_ArkUI_PanGesture_GetOffsetY(const ArkUI_GestureEvent* event)](#oh_arkui_pangesture_getoffsety) | - | Obtains the relative offset of a pan gesture along the y-axis. |
| [float OH_ArkUI_SwipeGesture_GetAngle(const ArkUI_GestureEvent* event)](#oh_arkui_swipegesture_getangle) | - | Angle of the swipe gesture, that is, the angle between the instantaneous direction of finger sliding and the positive horizontal direction. The unit is deg. With the positive horizontal direction as the reference, when the sliding direction is on the clockwise side of the positive horizontal direction, the angle ranges from 0 to 180 degrees; when on the counterclockwise side, the angle ranges from 0 to –180 degrees. |
| [float OH_ArkUI_SwipeGesture_GetVelocity(const ArkUI_GestureEvent* event)](#oh_arkui_swipegesture_getvelocity) | - | Obtains the average velocity of all fingers used in the swipe gesture. |
| [float OH_ArkUI_RotationGesture_GetAngle(const ArkUI_GestureEvent* event)](#oh_arkui_rotationgesture_getangle) | - | Obtains the angle information of a rotation gesture. |
| [float OH_ArkUI_PinchGesture_GetScale(const ArkUI_GestureEvent* event)](#oh_arkui_pinchgesture_getscale) | - | Obtains the scale ratio of a pinch gesture. |
| [float OH_ArkUI_PinchGesture_GetCenterX(const ArkUI_GestureEvent* event)](#oh_arkui_pinchgesture_getcenterx) | - | Obtains the x-coordinate of the center of the pinch gesture, in vp, relative to the upper left corner of the current component. |
| [float OH_ArkUI_PinchGesture_GetCenterY(const ArkUI_GestureEvent* event)](#oh_arkui_pinchgesture_getcentery) | - | Obtains the y-coordinate of the center of the pinch gesture, in vp, relative to the upper left corner of the current component. |
| [ArkUI_NodeHandle OH_ArkUI_GestureEvent_GetNode(const ArkUI_GestureEvent* event)](#oh_arkui_gestureevent_getnode) | - | Obtains the ArkUI component to which the gesture is bound. |
| [int32_t OH_ArkUI_GetResponseRecognizersFromInterruptInfo(const ArkUI_GestureInterruptInfo* event, ArkUI_GestureRecognizerHandleArray* responseChain, int32_t* count)](#oh_arkui_getresponserecognizersfrominterruptinfo) | - | Obtains information about a gesture response chain. |
| [int32_t OH_ArkUI_SetGestureRecognizerEnabled(ArkUI_GestureRecognizer* recognizer, bool enabled)](#oh_arkui_setgesturerecognizerenabled) | - | Sets the enabled state of a gesture recognizer. |
| [int32_t OH_ArkUI_SetGestureRecognizerLimitFingerCount(ArkUI_GestureRecognizer* recognizer, bool limitFingerCount)](#oh_arkui_setgesturerecognizerlimitfingercount) | - | Sets whether to enable strict finger count checking. If this feature is enabled and the actual number of touch fingers does not match the set number, the gesture recognition fails. |
| [bool OH_ArkUI_GetGestureRecognizerEnabled(ArkUI_GestureRecognizer* recognizer)](#oh_arkui_getgesturerecognizerenabled) | - | Obtains the enabled state of a gesture recognizer. |
| [int32_t OH_ArkUI_GetGestureRecognizerState(ArkUI_GestureRecognizer* recognizer, ArkUI_GestureRecognizerState* state)](#oh_arkui_getgesturerecognizerstate) | - | Obtains the state of a gesture recognizer. |
| [int32_t OH_ArkUI_GetGestureEventTargetInfo(ArkUI_GestureRecognizer* recognizer, ArkUI_GestureEventTargetInfo** info)](#oh_arkui_getgestureeventtargetinfo) | - | Obtains the information about a gesture event target. |
| [int32_t OH_ArkUI_GestureEventTargetInfo_IsScrollBegin(ArkUI_GestureEventTargetInfo* info, bool* ret)](#oh_arkui_gestureeventtargetinfo_isscrollbegin) | - | Obtains whether this scrollable container component is scrolled to the top. |
| [int32_t OH_ArkUI_GestureEventTargetInfo_IsScrollEnd(ArkUI_GestureEventTargetInfo* info, bool* ret)](#oh_arkui_gestureeventtargetinfo_isscrollend) | - | Obtains whether this scrollable container component is scrolled to the bottom. |
| [int32_t OH_ArkUI_GetPanGestureDirectionMask(ArkUI_GestureRecognizer* recognizer, ArkUI_GestureDirectionMask* directionMask)](#oh_arkui_getpangesturedirectionmask) | - | Obtains the direction of a pan gesture. |
| [bool OH_ArkUI_IsBuiltInGesture(ArkUI_GestureRecognizer* recognizer)](#oh_arkui_isbuiltingesture) | - | Obtains whether a gesture is a built-in gesture. |
| [int32_t OH_ArkUI_GetGestureTag(ArkUI_GestureRecognizer* recognizer, char* buffer, int32_t bufferSize, int32_t* result)](#oh_arkui_getgesturetag) | - | Obtains the tag of a gesture recognizer. |
| [int32_t OH_ArkUI_GetGestureBindNodeId(ArkUI_GestureRecognizer* recognizer, char* nodeId, int32_t size, int32_t* result)](#oh_arkui_getgesturebindnodeid) | - | Obtains the ID of the component linked to a gesture recognizer. |
| [bool OH_ArkUI_IsGestureRecognizerValid(ArkUI_GestureRecognizer* recognizer)](#oh_arkui_isgesturerecognizervalid) | - | Obtains whether a gesture recognizer is valid. |
| [void* OH_ArkUI_ParallelInnerGestureEvent_GetUserData(ArkUI_ParallelInnerGestureEvent* event)](#oh_arkui_parallelinnergestureevent_getuserdata) | - | Obtains custom data in the parallel built-in gesture event. |
| [ArkUI_GestureRecognizer* OH_ArkUI_ParallelInnerGestureEvent_GetCurrentRecognizer(ArkUI_ParallelInnerGestureEvent* event)](#oh_arkui_parallelinnergestureevent_getcurrentrecognizer) | - | Obtains the current gesture recognizer in a parallel built-in gesture event. |
| [int32_t OH_ArkUI_ParallelInnerGestureEvent_GetConflictRecognizers(ArkUI_ParallelInnerGestureEvent* event, ArkUI_GestureRecognizerHandleArray* array, int32_t* size)](#oh_arkui_parallelinnergestureevent_getconflictrecognizers) | - | Obtains the conflicting gesture recognizers in a parallel built-in gesture event. |
| [int32_t OH_ArkUI_SetArkUIGestureRecognizerDisposeNotify(ArkUI_GestureRecognizer* recognizer, ArkUI_GestureRecognizerDisposeNotifyCallback callback, void* userData)](#oh_arkui_setarkuigesturerecognizerdisposenotify) | - | Sets a callback function for notifying gesture recognizer destruction. |
| [int32_t OH_ArkUI_GetGestureParam_DirectMask(ArkUI_GestureRecognizer* recognizer, ArkUI_GestureDirectionMask* directMask)](#oh_arkui_getgestureparam_directmask) | - | Obtains the swipe direction of a gesture recognizer. |
| [int32_t OH_ArkUI_GetGestureParam_FingerCount(ArkUI_GestureRecognizer* recognizer, int* finger)](#oh_arkui_getgestureparam_fingercount) | - | Obtains the number of fingers used by a gesture recognizer. |
| [int32_t OH_ArkUI_GetGestureParam_limitFingerCount(ArkUI_GestureRecognizer* recognizer, bool* isLimited)](#oh_arkui_getgestureparam_limitfingercount) | - | Checks whether a gesture recognizer has a finger count limit. |
| [int32_t OH_ArkUI_GetGestureParam_repeat(ArkUI_GestureRecognizer* recognizer, bool* isRepeat)](#oh_arkui_getgestureparam_repeat) | - | Checks whether a gesture recognizer continuously triggers event callbacks. |
| [int32_t OH_ArkUI_GetGestureParam_distance(ArkUI_GestureRecognizer* recognizer, double* distance)](#oh_arkui_getgestureparam_distance) | - | Obtains the allowed movement distance range for a gesture recognizer. |
| [int32_t OH_ArkUI_GetGestureParam_speed(ArkUI_GestureRecognizer* recognizer, double* speed)](#oh_arkui_getgestureparam_speed) | - | Obtains the minimum swipe speed recognized by a gesture recognizer. |
| [int32_t OH_ArkUI_GetGestureParam_duration(ArkUI_GestureRecognizer* recognizer, int* duration)](#oh_arkui_getgestureparam_duration) | - | Obtains the minimum duration required to trigger a long press by a gesture recognizer. |
| [int32_t OH_ArkUI_GetGestureParam_angle(ArkUI_GestureRecognizer* recognizer, double* angle)](#oh_arkui_getgestureparam_angle) | - | Obtains the minimum angle change required for a rotation gesture to be recognized by a gesture recognizer. |
| [int32_t OH_ArkUI_GetGestureParam_distanceThreshold(ArkUI_GestureRecognizer* recognizer, double* distanceThreshold)](#oh_arkui_getgestureparam_distancethreshold) | - | Obtains the movement threshold distance for gesture recognition. |
| [ArkUI_ErrorCode OH_ArkUI_LongPressGesture_GetAllowableMovement(ArkUI_GestureRecognizer* recognizer, double* allowableMovement)](#oh_arkui_longpressgesture_getallowablemovement) | - | Obtains the maximum movement distance allowed for gesture recognition by the long press gesture recognizer. |
| [ArkUI_ErrorCode OH_ArkUI_PanGesture_SetDistanceMap(ArkUI_GestureRecognizer* recognizer, int size, int* toolTypeArray, double* distanceArray)](#oh_arkui_pangesture_setdistancemap) | - | Sets the minimum sliding distance threshold mapping for gesture recognition. |
| [ArkUI_ErrorCode OH_ArkUI_PanGesture_GetDistanceByToolType(ArkUI_GestureRecognizer* recognizer, int toolType, double* distance)](#oh_arkui_pangesture_getdistancebytooltype) | - | Obtains the movement distance threshold for gesture recognition for a specific input device type. This API only returns values for device types previously set using **OH_ArkUI_PanGesture_SetDistanceMap**. The default movement distance threshold can be obtained by querying the [UI_INPUT_EVENT_TOOL_TYPE_UNKNOWN](capi-ui-input-event-h.md#anonymous1) type. Other types that have not been set are not returned. |
| [ArkUI_ErrorCode OH_ArkUI_SetTouchTestDoneCallback(ArkUI_NodeHandle node, void* userData, void (\*touchTestDone)(ArkUI_GestureEvent* event, ArkUI_GestureRecognizerHandleArray recognizers, int32_t count, void* userData))](#oh_arkui_settouchtestdonecallback) | - | Registers a callback that is executed after all gesture recognizers are collected. When the user begins touching the screen, the system performs hit testing and collects gesture recognizers based on the touch location. Subsequently, before processing any move events, the component can use this API to determine the gesture recognizers that will participate in and compete for recognition. |
| [void* OH_ArkUI_GestureInterrupter_GetUserData(ArkUI_GestureInterruptInfo* event)](#oh_arkui_gestureinterrupter_getuserdata) | - | Obtains the custom data from a gesture interruption event. |
| [ArkUI_ErrorCode OH_ArkUI_PreventGestureRecognizerBegin(ArkUI_GestureRecognizer* recognizer)](#oh_arkui_preventgesturerecognizerbegin) | - | Prevents a gesture recognizer from participating in the current gesture recognition before all fingers are lifted. If the system has already determined the result of the gesture recognizer (regardless of success or failure), calling this API will be ineffective. |
| [ArkUI_ErrorCode OH_ArkUI_LongPressGesture_SetAllowableMovement(ArkUI_GestureRecognizer* recognizer, double allowableMovement)](#oh_arkui_longpressgesture_setallowablemovement) | - | Sets the maximum movement distance allowed for gesture recognition by the long press gesture recognizer. |
| [ArkUI_ErrorCode OH_ArkUI_GestureCollectInterceptInfo_GetResponseRecognizers(const ArkUI_GestureCollectInterceptInfo* info, ArkUI_GestureRecognizerHandleArray* array, int32_t* size)](#oh_arkui_gesturecollectinterceptinfo_getresponserecognizers) | - | Obtains gesture recognizer handles from gesture collection interception information. |
| [ArkUI_ErrorCode OH_ArkUI_GestureCollectInterceptInfo_GetTouchRecognizers(const ArkUI_GestureCollectInterceptInfo* info, ArkUI_TouchRecognizerHandleArray* recognizers, int32_t* size)](#oh_arkui_gesturecollectinterceptinfo_gettouchrecognizers) | - | Obtains touch recognizer handles from gesture collection interception information. |
| [ArkUI_ErrorCode OH_ArkUI_GestureCollectInterceptInfo_SetGestureCollectIntervention(ArkUI_GestureCollectInterceptInfo* info, OH_ArkUI_GestureCollectIntervention intervention)](#oh_arkui_gesturecollectinterceptinfo_setgesturecollectintervention) | - | Sets the intervention mode for gesture collection. |
| [ArkUI_ErrorCode OH_ArkUI_GetGestureBindNodeUniqueId(const ArkUI_GestureRecognizer* recognizer, int32_t* uniqueId)](#oh_arkui_getgesturebindnodeuniqueid) | - | Obtains the unique ID of the component bound to a gesture recognizer. |
| [bool OH_ArkUI_TouchRecognizer_IsHostBelongsTo(const ArkUI_TouchRecognizerHandle recognizer, int32_t uniqueId)](#oh_arkui_touchrecognizer_ishostbelongsto) | - | Checks whether the node bound to the touch recognizer is a descendant node of the passed component. |
| [bool OH_ArkUI_GestureRecognizer_IsHostBelongsTo(const ArkUI_GestureRecognizer* recognizer, int32_t uniqueId)](#oh_arkui_gesturerecognizer_ishostbelongsto) | - | Checks whether the node bound to the gesture recognizer is a descendant node of the passed component. |

### Variable

| Name | Description |
| -- | -- |
| uint32_t ArkUI_GestureEventActionTypeMask | Defines a set of gesture event types. Example: ArkUI_GestureEventActionTypeMask actions = GESTURE_EVENT_ACTION_ACCEPT \\| GESTURE_EVENT_ACTION_UPDATE<br>**Since**: 12 |
| uint32_t ArkUI_GestureDirectionMask | Defines a set of gesture directions. <br>Example: ArkUI_GestureDirectionMask directions = GESTURE_DIRECTION_LEFT \\| GESTURE_DIRECTION_RIGHT <br>This example indicates that the leftward and rightward directions are supported.<br>**Since**: 12 |
| ArkUI_GestureRecognizer* ArkUI_GestureRecognizerHandle | Defines the gesture recognizer handle.<br>**Since**: 12 |
| ArkUI_GestureRecognizerHandle* ArkUI_GestureRecognizerHandleArray | Defines the gesture recognizer handle array.<br>**Since**: 12 |
| ArkUI_TouchRecognizer* ArkUI_TouchRecognizerHandle | Defines a touch recognizer handle.<br>**Since**: 15 |
| ArkUI_TouchRecognizerHandle* ArkUI_TouchRecognizerHandleArray | Defines an array of touch recognizer handle.<br>**Since**: 15 |
| void (*ArkUI_GestureRecognizerDisposeNotifyCallback)(ArkUI_GestureRecognizer* recognizer, void* userData) | Defines a callback function for notifying gesture recognizer destruction.<br>**Since**: 12 |

## Enum type description

### ArkUI_GestureEventActionType

```c
enum ArkUI_GestureEventActionType
```

**Description**

Enumerates gesture event types.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| GESTURE_EVENT_ACTION_ACCEPT = 0x01 | Triggered. |
| GESTURE_EVENT_ACTION_UPDATE = 0x02 | Updated. |
| GESTURE_EVENT_ACTION_END = 0x04 | Ended. |
| GESTURE_EVENT_ACTION_CANCEL = 0x08 | Canceled. |

### ArkUI_GesturePriority

```c
enum ArkUI_GesturePriority
```

**Description**

Enumerates gesture event modes.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| NORMAL = 0 | Normal. |
| PRIORITY = 1 | High priority. |
| PARALLEL = 2 | Parallel. |

### ArkUI_GroupGestureMode

```c
enum ArkUI_GroupGestureMode
```

**Description**

Enumerates gesture group modes.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| SEQUENTIAL_GROUP = 0 | Sequential recognition. Gestures are recognized in the registration sequence until all gestures are recognized successfully. Once one gesture fails to be recognized, all subsequent gestures fail to be recognized. Only the last gesture in the gesture group can respond to the end event. |
| PARALLEL_GROUP = 1 | Parallel recognition. Registered gestures are recognized concurrently until all gestures are recognized. The recognition result of each gesture does not affect each other. |
| EXCLUSIVE_GROUP = 2 | Exclusive recognition. Registered gestures are identified concurrently. If one gesture is successfully recognized, gesture recognition ends. |

### ArkUI_GestureDirection

```c
enum ArkUI_GestureDirection
```

**Description**

Enumerates gesture directions.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| GESTURE_DIRECTION_ALL = 0b1111 | All directions. |
| GESTURE_DIRECTION_HORIZONTAL = 0b0011 | Horizontal direction. |
| GESTURE_DIRECTION_VERTICAL = 0b1100 | Vertical direction. |
| GESTURE_DIRECTION_LEFT = 0b0001 | Leftward. |
| GESTURE_DIRECTION_RIGHT = 0b0010 | Rightward. |
| GESTURE_DIRECTION_UP = 0b0100 | Upward. |
| GESTURE_DIRECTION_DOWN = 0b1000 | Downward. |
| GESTURE_DIRECTION_NONE = 0 | None. |

### ArkUI_GestureMask

```c
enum ArkUI_GestureMask
```

**Description**

Enumerates gesture masking modes.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| NORMAL_GESTURE_MASK = 0 | The gestures of child components are enabled and recognized based on the default gesture recognition sequence. |
| IGNORE_INTERNAL_GESTURE_MASK | The gestures of child components are disabled, including the built-in gestures. |

### ArkUI_GestureRecognizerType

```c
enum ArkUI_GestureRecognizerType
```

**Description**

Enumerates gesture recognizer types.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| TAP_GESTURE = 0 | Tap. |
| LONG_PRESS_GESTURE | Long press. |
| PAN_GESTURE | Pan. |
| PINCH_GESTURE | Pinch. |
| ROTATION_GESTURE | Rotate. |
| SWIPE_GESTURE | Swipe. |
| GROUP_GESTURE | A group of gestures. |
| CLICK_GESTURE |  |
| DRAG_DROP |  |

### ArkUI_GestureInterruptResult

```c
enum ArkUI_GestureInterruptResult
```

**Description**

Enumerates gesture interruption results.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| GESTURE_INTERRUPT_RESULT_CONTINUE = 0 | The gesture recognition process continues. |
| GESTURE_INTERRUPT_RESULT_REJECT | The gesture recognition process is paused. |

### ArkUI_GestureRecognizerState

```c
enum ArkUI_GestureRecognizerState
```

**Description**

Enumerates the gesture recognizer states.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_GESTURE_RECOGNIZER_STATE_READY = 0 | Ready. |
| ARKUI_GESTURE_RECOGNIZER_STATE_DETECTING = 1 | Detecting. |
| ARKUI_GESTURE_RECOGNIZER_STATE_PENDING = 2 | Pending. |
| ARKUI_GESTURE_RECOGNIZER_STATE_BLOCKED = 3 | Blocked. |
| ARKUI_GESTURE_RECOGNIZER_STATE_SUCCESSFUL = 4 | Successful. |
| ARKUI_GESTURE_RECOGNIZER_STATE_FAILED = 5 | Failed. |

### OH_ArkUI_GestureCollectIntervention

```c
enum OH_ArkUI_GestureCollectIntervention
```

**Description**

Defines the intervention types for gesture and event collection.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

| Enum item | Description |
| -- | -- |
| OH_ARKUI_GESTURE_COLLECT_INTERVENTION_CONTINUE = 0 | Continues the normal gesture and event collection flow. No intervention is performed.<br>**Since**: 26.0.0 |
| OH_ARKUI_GESTURE_COLLECT_INTERVENTION_DISCARD_LOWER = 1 | Discards all low-priority gestures and events to be collected. <br>The gestures of the left sibling node and ancestor nodes (parent nodes and above) are discarded. <br>Only the gestures already collected on the current node and higher-priority nodes are retained.<br>**Since**: 26.0.0 |
| OH_ARKUI_GESTURE_COLLECT_INTERVENTION_DISCARD_HIGHER = 2 | Discards all collected high-priority gestures and events. <br>The gestures of the right sibling node and the current node are discarded. <br>Continues processing the collection flow for lower-priority gestures (left sibling and ancestor nodes).<br>**Since**: 26.0.0 |
| OH_ARKUI_GESTURE_COLLECT_INTERVENTION_DISCARD_SELF = 3 | Discards the gestures and events of the current node. <br>The gestures and events of the current node are excluded from the gesture tree. <br>The gestures of the sibling nodes (left and right) and the ancestor nodes are still collected.<br>**Since**: 26.0.0 |
| OH_ARKUI_GESTURE_COLLECT_INTERVENTION_DISCARD_LOWER_PRIORITY_SIBLINGS = 4 | Discards the gestures and events to be collected from the left sibling node. <br>The gestures and events of the current node and the collected gestures and events of the right sibling node are retained. <br>Continues processing the collection flow for the parent and ancestor nodes.<br>**Since**: 26.0.0 |


## Function description

### ArkUI_GestureRecognizerDisposeNotifyCallback()

```c
typedef void (*ArkUI_GestureRecognizerDisposeNotifyCallback)(ArkUI_GestureRecognizer* recognizer, void* userData)
```

**Description**

Defines a callback function for notifying gesture recognizer destruction.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)\* recognizer | Pointer to the gesture recognizer instance. |
| void\* userData | Pointer to user-defined data. |

### OH_ArkUI_GestureInterruptInfo_GetSystemFlag()

```c
bool OH_ArkUI_GestureInterruptInfo_GetSystemFlag(const ArkUI_GestureInterruptInfo* event)
```

**Description**

Checks whether a gesture is a built-in gesture of the component.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_GestureInterruptInfo](capi-arkui-nativemodule-arkui-gestureinterruptinfo.md)* event | Indicates the pointer to the gesture interruption information. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns <b>true</b> if the gesture is a built-in gesture; returns <b>false</b> otherwise. |

### OH_ArkUI_GestureInterruptInfo_GetRecognizer()

```c
ArkUI_GestureRecognizer* OH_ArkUI_GestureInterruptInfo_GetRecognizer(const ArkUI_GestureInterruptInfo* event)
```

**Description**

Obtains the pointer to the interrupted gesture recognizer.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_GestureInterruptInfo](capi-arkui-nativemodule-arkui-gestureinterruptinfo.md)* event | Pointer to the gesture interruption callback event. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_GestureRecognizer*](capi-arkui-nativemodule-arkui-gesturerecognizer.md) | Pointer to the interrupted gesture recognizer. |

### OH_ArkUI_GestureInterruptInfo_GetGestureEvent()

```c
ArkUI_GestureEvent* OH_ArkUI_GestureInterruptInfo_GetGestureEvent(const ArkUI_GestureInterruptInfo* event)
```

**Description**

Obtains the pointer to the interrupted gesture event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_GestureInterruptInfo](capi-arkui-nativemodule-arkui-gestureinterruptinfo.md)* event | Pointer to the gesture interruption callback event. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_GestureEvent*](capi-arkui-nativemodule-arkui-gestureevent.md) | Pointer to the interrupted gesture event. |

### OH_ArkUI_GestureInterruptInfo_GetSystemRecognizerType()

```c
int32_t OH_ArkUI_GestureInterruptInfo_GetSystemRecognizerType(const ArkUI_GestureInterruptInfo* event)
```

**Description**

Obtains the type of the system built-in gesture to trigger.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_GestureInterruptInfo](capi-arkui-nativemodule-arkui-gestureinterruptinfo.md)* event | Pointer to the gesture interruption callback event. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Type of the system built-in gesture to trigger. The value is defined in [ArkUI_GestureRecognizerType](capi-native-gesture-h.md#arkui_gesturerecognizertype).      If the triggered gesture is not a built-in gesture, -1 is returned. |

### OH_ArkUI_GestureInterruptInfo_GetTouchRecognizers()

```c
int32_t OH_ArkUI_GestureInterruptInfo_GetTouchRecognizers(const ArkUI_GestureInterruptInfo* info, ArkUI_TouchRecognizerHandleArray* recognizers, int32_t* size)
```

**Description**

Obtains touch recognizers from gesture interruption information.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_GestureInterruptInfo](capi-arkui-nativemodule-arkui-gestureinterruptinfo.md)* info | Pointer to the gesture interruption information. |
| ArkUI_TouchRecognizerHandleArray* recognizers | Pointer to the touch recognizer handle array. |
| int32_t* size | Pointer to the size of the touch recognizer array. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      <br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_TouchRecognizer_GetNodeHandle()

```c
ArkUI_NodeHandle OH_ArkUI_TouchRecognizer_GetNodeHandle(const ArkUI_TouchRecognizerHandle recognizer)
```

**Description**

Obtains the component handle corresponding to a touch recognizer.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| const ArkUI_TouchRecognizerHandle recognizer | Handle to the touch recognizer. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_NodeHandle | Component handle corresponding to the touch recognizer. |

### OH_ArkUI_TouchRecognizer_CancelTouch()

```c
int32_t OH_ArkUI_TouchRecognizer_CancelTouch(ArkUI_TouchRecognizerHandle recognizer, ArkUI_GestureInterruptInfo* info)
```

**Description**

Sends a cancel touch event to a touch recognizer in a gesture interruption callback.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_TouchRecognizerHandle recognizer | Handle to the touch recognizer. |
| [ArkUI_GestureInterruptInfo](capi-arkui-nativemodule-arkui-gestureinterruptinfo.md)* info | Pointer to the gesture interruption information. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      <br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_GestureEvent_GetActionType()

```c
ArkUI_GestureEventActionType OH_ArkUI_GestureEvent_GetActionType(const ArkUI_GestureEvent* event)
```

**Description**

Obtains the gesture event type.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_GestureEvent](capi-arkui-nativemodule-arkui-gestureevent.md)* event | Pointer to the gesture event. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_GestureEventActionType](capi-native-gesture-h.md#arkui_gestureeventactiontype) | Type of the gesture event. |

### OH_ArkUI_GestureEvent_GetRawInputEvent()

```c
const ArkUI_UIInputEvent* OH_ArkUI_GestureEvent_GetRawInputEvent(const ArkUI_GestureEvent* event)
```

**Description**

Obtains gesture input.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_GestureEvent](capi-arkui-nativemodule-arkui-gestureevent.md)* event | Pointer to the gesture event. |

**Returns**:

| Type | Description |
| -- | -- |
| const ArkUI_UIInputEvent* | Pointer to the input event of the gesture event. |

### OH_ArkUI_LongPress_GetRepeatCount()

```c
int32_t OH_ArkUI_LongPress_GetRepeatCount(const ArkUI_GestureEvent* event)
```

**Description**

Checks whether the event is a repeated trigger event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_GestureEvent](capi-arkui-nativemodule-arkui-gestureevent.md)* event | Pointer to the gesture event. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Whether the event is a repeated trigger event. The value 1 means that the event is a repeated trigger      event, and 0 means the opposite. |

### OH_ArkUI_PanGesture_GetVelocity()

```c
float OH_ArkUI_PanGesture_GetVelocity(const ArkUI_GestureEvent* event)
```

**Description**

Obtains the velocity of a pan gesture along the main axis.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_GestureEvent](capi-arkui-nativemodule-arkui-gestureevent.md)* event | Pointer to the gesture event. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Velocity of the pan gesture along the main axis, in px/s. The value is the square root of the sum of the      squares of the velocity on the x-axis and y-axis. |

### OH_ArkUI_PanGesture_GetVelocityX()

```c
float OH_ArkUI_PanGesture_GetVelocityX(const ArkUI_GestureEvent* event)
```

**Description**

Obtains the velocity of a pan gesture along the x-axis.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_GestureEvent](capi-arkui-nativemodule-arkui-gestureevent.md)* event | Pointer to the gesture event. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Velocity of the pan gesture along the x-axis, in px/s. |

### OH_ArkUI_PanGesture_GetVelocityY()

```c
float OH_ArkUI_PanGesture_GetVelocityY(const ArkUI_GestureEvent* event)
```

**Description**

Obtains the velocity of a pan gesture along the y-axis.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_GestureEvent](capi-arkui-nativemodule-arkui-gestureevent.md)* event | Pointer to the gesture event. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Velocity of the pan gesture along the y-axis, in px/s. |

### OH_ArkUI_PanGesture_GetOffsetX()

```c
float OH_ArkUI_PanGesture_GetOffsetX(const ArkUI_GestureEvent* event)
```

**Description**

Obtains the relative offset of a pan gesture along the x-axis.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_GestureEvent](capi-arkui-nativemodule-arkui-gestureevent.md)* event | Pointer to the gesture event. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Relative offset of the gesture along the x-axis, in px. |

### OH_ArkUI_PanGesture_GetOffsetY()

```c
float OH_ArkUI_PanGesture_GetOffsetY(const ArkUI_GestureEvent* event)
```

**Description**

Obtains the relative offset of a pan gesture along the y-axis.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_GestureEvent](capi-arkui-nativemodule-arkui-gestureevent.md)* event | Pointer to the gesture event. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Relative offset of the gesture along the y-axis, in px. |

### OH_ArkUI_SwipeGesture_GetAngle()

```c
float OH_ArkUI_SwipeGesture_GetAngle(const ArkUI_GestureEvent* event)
```

**Description**

Angle of the swipe gesture, that is, the angle between the instantaneous direction of finger sliding and the positive horizontal direction. The unit is deg. With the positive horizontal direction as the reference, when the sliding direction is on the clockwise side of the positive horizontal direction, the angle ranges from 0 to 180 degrees; when on the counterclockwise side, the angle ranges from 0 to –180 degrees.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_GestureEvent](capi-arkui-nativemodule-arkui-gestureevent.md)* event | Pointer to the gesture event. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Angle of the swipe gesture, which is the result obtained based on the aforementioned formula.  The unit is deg. |

### OH_ArkUI_SwipeGesture_GetVelocity()

```c
float OH_ArkUI_SwipeGesture_GetVelocity(const ArkUI_GestureEvent* event)
```

**Description**

Obtains the average velocity of all fingers used in the swipe gesture.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_GestureEvent](capi-arkui-nativemodule-arkui-gestureevent.md)* event | Pointer to the gesture event. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Average velocity of all fingers used in the swipe gesture, in px/s. |

### OH_ArkUI_RotationGesture_GetAngle()

```c
float OH_ArkUI_RotationGesture_GetAngle(const ArkUI_GestureEvent* event)
```

**Description**

Obtains the angle information of a rotation gesture.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_GestureEvent](capi-arkui-nativemodule-arkui-gestureevent.md)* event | Pointer to the gesture event. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Rotation angle. The unit is deg. |

### OH_ArkUI_PinchGesture_GetScale()

```c
float OH_ArkUI_PinchGesture_GetScale(const ArkUI_GestureEvent* event)
```

**Description**

Obtains the scale ratio of a pinch gesture.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_GestureEvent](capi-arkui-nativemodule-arkui-gestureevent.md)* event | Pointer to the gesture event. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Scale factor. |

### OH_ArkUI_PinchGesture_GetCenterX()

```c
float OH_ArkUI_PinchGesture_GetCenterX(const ArkUI_GestureEvent* event)
```

**Description**

Obtains the x-coordinate of the center of the pinch gesture, in vp, relative to the upper left corner of the current component.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_GestureEvent](capi-arkui-nativemodule-arkui-gestureevent.md)* event | Pointer to the gesture event. |

**Returns**:

| Type | Description |
| -- | -- |
| float | X-coordinate of the center of the pinch gesture, in px, relative to the upper left corner of the current      component. |

### OH_ArkUI_PinchGesture_GetCenterY()

```c
float OH_ArkUI_PinchGesture_GetCenterY(const ArkUI_GestureEvent* event)
```

**Description**

Obtains the y-coordinate of the center of the pinch gesture, in vp, relative to the upper left corner of the current component.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_GestureEvent](capi-arkui-nativemodule-arkui-gestureevent.md)* event | Pointer to the gesture event. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Y-coordinate of the center of the pinch gesture, in px, relative to the upper left corner of the current      component. |

### OH_ArkUI_GestureEvent_GetNode()

```c
ArkUI_NodeHandle OH_ArkUI_GestureEvent_GetNode(const ArkUI_GestureEvent* event)
```

**Description**

Obtains the ArkUI component to which the gesture is bound.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_GestureEvent](capi-arkui-nativemodule-arkui-gestureevent.md)* event | Pointer to the gesture event. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_NodeHandle | ArkUI component to which the gesture is bound. Returns NULL if the event is invalid. |

### OH_ArkUI_GetResponseRecognizersFromInterruptInfo()

```c
int32_t OH_ArkUI_GetResponseRecognizersFromInterruptInfo(const ArkUI_GestureInterruptInfo* event, ArkUI_GestureRecognizerHandleArray* responseChain, int32_t* count)
```

**Description**

Obtains information about a gesture response chain.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_GestureInterruptInfo](capi-arkui-nativemodule-arkui-gestureinterruptinfo.md)* event | Pointer to the gesture interruption callback event. |
| ArkUI_GestureRecognizerHandleArray* responseChain | Pointer to an array of gesture recognizer handles on the response chain. |
| int32_t* count | Pointer to the number of gesture recognizer handles on the response chain. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      <br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_SetGestureRecognizerEnabled()

```c
int32_t OH_ArkUI_SetGestureRecognizerEnabled(ArkUI_GestureRecognizer* recognizer, bool enabled)
```

**Description**

Sets the enabled state of a gesture recognizer.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance. |
| bool enabled | Enabled state. The value **true** means that the gesture recognizer is enabled, and **false** means the opposite. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      <br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_SetGestureRecognizerLimitFingerCount()

```c
int32_t OH_ArkUI_SetGestureRecognizerLimitFingerCount(ArkUI_GestureRecognizer* recognizer, bool limitFingerCount)
```

**Description**

Sets whether to enable strict finger count checking. If this feature is enabled and the actual number of touch fingers does not match the set number, the gesture recognition fails.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance. |
| bool limitFingerCount | Whether to enable strict finger count checking. <br>**true**: Enforce the exact number of fingers touching the screen. <br>**false**: Do not enforce the exact number of fingers touching the screen. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      <br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_GetGestureRecognizerEnabled()

```c
bool OH_ArkUI_GetGestureRecognizerEnabled(ArkUI_GestureRecognizer* recognizer)
```

**Description**

Obtains the enabled state of a gesture recognizer.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | true: enabled.      <br>false: disabled. |

### OH_ArkUI_GetGestureRecognizerState()

```c
int32_t OH_ArkUI_GetGestureRecognizerState(ArkUI_GestureRecognizer* recognizer, ArkUI_GestureRecognizerState* state)
```

**Description**

Obtains the state of a gesture recognizer.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance. |
| [ArkUI_GestureRecognizerState](capi-native-gesture-h.md#arkui_gesturerecognizerstate)* state | Pointer to the state of the gesture recognizer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      <br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_GetGestureEventTargetInfo()

```c
int32_t OH_ArkUI_GetGestureEventTargetInfo(ArkUI_GestureRecognizer* recognizer, ArkUI_GestureEventTargetInfo** info)
```

**Description**

Obtains the information about a gesture event target.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance. |
| [ArkUI_GestureEventTargetInfo](capi-arkui-nativemodule-arkui-gestureeventtargetinfo.md)** info | Double pointer to the information about a gesture event target. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      <br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_GestureEventTargetInfo_IsScrollBegin()

```c
int32_t OH_ArkUI_GestureEventTargetInfo_IsScrollBegin(ArkUI_GestureEventTargetInfo* info, bool* ret)
```

**Description**

Obtains whether this scrollable container component is scrolled to the top.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_GestureEventTargetInfo](capi-arkui-nativemodule-arkui-gestureeventtargetinfo.md)* info | Pointer to the information about a gesture event target. |
| bool* ret | Pointer to the **ret** parameter indicating whether this scrollable container component is scrolled to the top. The value **true** means that the component is scrolled to the top, and **false** means the opposite. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      <br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs.      <br>Returns [ARKUI_ERROR_CODE_NON_SCROLLABLE_CONTAINER](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the component is not a scrollable container. |

### OH_ArkUI_GestureEventTargetInfo_IsScrollEnd()

```c
int32_t OH_ArkUI_GestureEventTargetInfo_IsScrollEnd(ArkUI_GestureEventTargetInfo* info, bool* ret)
```

**Description**

Obtains whether this scrollable container component is scrolled to the bottom.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_GestureEventTargetInfo](capi-arkui-nativemodule-arkui-gestureeventtargetinfo.md)* info | Pointer to the information about a gesture event target. |
| bool* ret | Pointer to the **ret** parameter indicating whether this scrollable container component is scrolled to the bottom. The value **true** means that the component is scrolled to the bottom, and **false** means the opposite. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      <br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs.      <br>Returns [ARKUI_ERROR_CODE_NON_SCROLLABLE_CONTAINER](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the component is not a scrollable container. |

### OH_ArkUI_GetPanGestureDirectionMask()

```c
int32_t OH_ArkUI_GetPanGestureDirectionMask(ArkUI_GestureRecognizer* recognizer, ArkUI_GestureDirectionMask* directionMask)
```

**Description**

Obtains the direction of a pan gesture.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance. |
| ArkUI_GestureDirectionMask* directionMask | Pointer to the pan direction. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      <br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_IsBuiltInGesture()

```c
bool OH_ArkUI_IsBuiltInGesture(ArkUI_GestureRecognizer* recognizer)
```

**Description**

Obtains whether a gesture is a built-in gesture.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | true: built-in gesture.      <br>false: non-built-in gesture. |

### OH_ArkUI_GetGestureTag()

```c
int32_t OH_ArkUI_GetGestureTag(ArkUI_GestureRecognizer* recognizer, char* buffer, int32_t bufferSize, int32_t* result)
```

**Description**

Obtains the tag of a gesture recognizer.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance. |
| char* buffer | Pointer to the output buffer. |
| int32_t bufferSize | Size of the output buffer. |
| int32_t* result | Pointer to the length of the copied string. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      <br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs.      <br>Returns [ARKUI_ERROR_CODE_BUFFER_SIZE_NOT_ENOUGH](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the buffer is not large enough. |

### OH_ArkUI_GetGestureBindNodeId()

```c
int32_t OH_ArkUI_GetGestureBindNodeId(ArkUI_GestureRecognizer* recognizer, char* nodeId, int32_t size, int32_t* result)
```

**Description**

Obtains the ID of the component linked to a gesture recognizer.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance. |
| char* nodeId | Pointer to the component ID. |
| int32_t size | Size of the output buffer. |
| int32_t* result | Pointer to the length of the copied string. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      <br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs.      <br>Returns [ARKUI_ERROR_CODE_BUFFER_SIZE_NOT_ENOUGH](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the buffer is not large enough. |

### OH_ArkUI_IsGestureRecognizerValid()

```c
bool OH_ArkUI_IsGestureRecognizerValid(ArkUI_GestureRecognizer* recognizer)
```

**Description**

Obtains whether a gesture recognizer is valid.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | true: The gesture recognizer is valid.      <br>false: The gesture recognizer is invalid. |

### OH_ArkUI_ParallelInnerGestureEvent_GetUserData()

```c
void* OH_ArkUI_ParallelInnerGestureEvent_GetUserData(ArkUI_ParallelInnerGestureEvent* event)
```

**Description**

Obtains custom data in the parallel built-in gesture event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ParallelInnerGestureEvent](capi-arkui-nativemodule-arkui-parallelinnergestureevent.md)* event | Pointer to the parallel built-in gesture event. |

**Returns**:

| Type | Description |
| -- | -- |
| void* | Pointer to user-defined data. |

### OH_ArkUI_ParallelInnerGestureEvent_GetCurrentRecognizer()

```c
ArkUI_GestureRecognizer* OH_ArkUI_ParallelInnerGestureEvent_GetCurrentRecognizer(ArkUI_ParallelInnerGestureEvent* event)
```

**Description**

Obtains the current gesture recognizer in a parallel built-in gesture event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ParallelInnerGestureEvent](capi-arkui-nativemodule-arkui-parallelinnergestureevent.md)* event | Pointer to the parallel built-in gesture event. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_GestureRecognizer*](capi-arkui-nativemodule-arkui-gesturerecognizer.md) | Pointer to the current gesture recognizer. |

### OH_ArkUI_ParallelInnerGestureEvent_GetConflictRecognizers()

```c
int32_t OH_ArkUI_ParallelInnerGestureEvent_GetConflictRecognizers(ArkUI_ParallelInnerGestureEvent* event, ArkUI_GestureRecognizerHandleArray* array, int32_t* size)
```

**Description**

Obtains the conflicting gesture recognizers in a parallel built-in gesture event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ParallelInnerGestureEvent](capi-arkui-nativemodule-arkui-parallelinnergestureevent.md)* event | Pointer to the parallel built-in gesture event. |
| ArkUI_GestureRecognizerHandleArray* array | Pointer to the array of conflicting gesture recognizers. |
| int32_t* size | Pointer to the size of the array of conflicting gesture recognizers. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      <br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_SetArkUIGestureRecognizerDisposeNotify()

```c
int32_t OH_ArkUI_SetArkUIGestureRecognizerDisposeNotify(ArkUI_GestureRecognizer* recognizer, ArkUI_GestureRecognizerDisposeNotifyCallback callback, void* userData)
```

**Description**

Sets a callback function for notifying gesture recognizer destruction.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance. |
| [ArkUI_GestureRecognizerDisposeNotifyCallback](capi-native-gesture-h.md#arkui_gesturerecognizerdisposenotifycallback) callback | Callback function for notifying gesture recognizer destruction. |
| void* userData | Pointer to user-defined data. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      <br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_GetGestureParam_DirectMask()

```c
int32_t OH_ArkUI_GetGestureParam_DirectMask(ArkUI_GestureRecognizer* recognizer, ArkUI_GestureDirectionMask* directMask)
```

**Description**

Obtains the swipe direction of a gesture recognizer.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance. |
| ArkUI_GestureDirectionMask* directMask | Pointer to the swipe direction of the gesture recognizer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      <br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_GetGestureParam_FingerCount()

```c
int32_t OH_ArkUI_GetGestureParam_FingerCount(ArkUI_GestureRecognizer* recognizer, int* finger)
```

**Description**

Obtains the number of fingers used by a gesture recognizer.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance. |
| int* finger | Pointer to the number of fingers used by the gesture recognizer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      <br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_GetGestureParam_limitFingerCount()

```c
int32_t OH_ArkUI_GetGestureParam_limitFingerCount(ArkUI_GestureRecognizer* recognizer, bool* isLimited)
```

**Description**

Checks whether a gesture recognizer has a finger count limit.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance. |
| bool* isLimited | Pointer to the parameter indicating whether the gesture recognizer has a finger count limit. **true** indicates that the gesture recognizer has a finger count limit. **false** indicates that the gesture recognizer does not have a finger count limit. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      <br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_GetGestureParam_repeat()

```c
int32_t OH_ArkUI_GetGestureParam_repeat(ArkUI_GestureRecognizer* recognizer, bool* isRepeat)
```

**Description**

Checks whether a gesture recognizer continuously triggers event callbacks.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance. |
| bool* isRepeat | Pointer to the parameter indicating whether the gesture recognizer continuously triggers event callbacks. The value **true** means to continuously trigger event callbacks, and false means the opposite. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      <br>Returns [ARKUI_ERROR_CODE_RECOGNIZER_TYPE_NOT_SUPPORTED](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the gesture recognizer type is not      supported. |

### OH_ArkUI_GetGestureParam_distance()

```c
int32_t OH_ArkUI_GetGestureParam_distance(ArkUI_GestureRecognizer* recognizer, double* distance)
```

**Description**

Obtains the allowed movement distance range for a gesture recognizer.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance. |
| double* distance | Pointer to the allowed movement distance range of the gesture recognizer. The unit is px. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      <br>Returns [ARKUI_ERROR_CODE_RECOGNIZER_TYPE_NOT_SUPPORTED](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the gesture recognizer type is not      supported. |

### OH_ArkUI_GetGestureParam_speed()

```c
int32_t OH_ArkUI_GetGestureParam_speed(ArkUI_GestureRecognizer* recognizer, double* speed)
```

**Description**

Obtains the minimum swipe speed recognized by a gesture recognizer.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance. |
| double* speed | Pointer to the minimum swipe speed recognized by the gesture recognizer. The unit is px/s. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      <br>Returns [ARKUI_ERROR_CODE_RECOGNIZER_TYPE_NOT_SUPPORTED](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the gesture recognizer type is not      supported. |

### OH_ArkUI_GetGestureParam_duration()

```c
int32_t OH_ArkUI_GetGestureParam_duration(ArkUI_GestureRecognizer* recognizer, int* duration)
```

**Description**

Obtains the minimum duration required to trigger a long press by a gesture recognizer.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance. |
| int* duration | Pointer to the minimum duration for a long press. The unit is ms. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      <br>Returns [ARKUI_ERROR_CODE_RECOGNIZER_TYPE_NOT_SUPPORTED](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the gesture recognizer type is not      supported. |

### OH_ArkUI_GetGestureParam_angle()

```c
int32_t OH_ArkUI_GetGestureParam_angle(ArkUI_GestureRecognizer* recognizer, double* angle)
```

**Description**

Obtains the minimum angle change required for a rotation gesture to be recognized by a gesture recognizer.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance. |
| double* angle | Pointer to the minimum angle change. The unit is deg. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      <br>Returns [ARKUI_ERROR_CODE_RECOGNIZER_TYPE_NOT_SUPPORTED](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the gesture recognizer type is not      supported. |

### OH_ArkUI_GetGestureParam_distanceThreshold()

```c
int32_t OH_ArkUI_GetGestureParam_distanceThreshold(ArkUI_GestureRecognizer* recognizer, double* distanceThreshold)
```

**Description**

Obtains the movement threshold distance for gesture recognition.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance. |
| distanceThresHold | Movement threshold. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <br>Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      <br>Returns [ARKUI_ERROR_CODE_RECOGNIZER_TYPE_NOT_SUPPORTED](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the gesture recognizer type is not      supported. |

### OH_ArkUI_LongPressGesture_GetAllowableMovement()

```c
ArkUI_ErrorCode OH_ArkUI_LongPressGesture_GetAllowableMovement(ArkUI_GestureRecognizer* recognizer, double* allowableMovement)
```

**Description**

Obtains the maximum movement distance allowed for gesture recognition by the long press gesture recognizer.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance. |
| double* allowableMovement | Pointer to the maximum movement distance allowed for gesture recognition by the long press gesture recognizer. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Result code.      <br>Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      <br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs.      <br>Returns [ARKUI_ERROR_CODE_RECOGNIZER_TYPE_NOT_SUPPORTED](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the gesture recognizer type is not      supported. |

### OH_ArkUI_PanGesture_SetDistanceMap()

```c
ArkUI_ErrorCode OH_ArkUI_PanGesture_SetDistanceMap(ArkUI_GestureRecognizer* recognizer, int size, int* toolTypeArray, double* distanceArray)
```

**Description**

Sets the minimum sliding distance threshold mapping for gesture recognition.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance. |
| int size | Size of the array of minimum sliding distance thresholds. |
| int* toolTypeArray | Pointer to the array of tool types for which thresholds are set. If a value other than [UI_INPUT_EVENT_TOOL_TYPE](capi-ui-input-event-h.md#anonymous1)_XXX is set, the setting does not take effect. |
| double* distanceArray | Pointer to the array of minimum sliding distances. The unit is px. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Result code.      <br>Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      <br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs.      <br>Returns [ARKUI_ERROR_CODE_RECOGNIZER_TYPE_NOT_SUPPORTED](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the gesture recognizer type is not      supported. |

### OH_ArkUI_PanGesture_GetDistanceByToolType()

```c
ArkUI_ErrorCode OH_ArkUI_PanGesture_GetDistanceByToolType(ArkUI_GestureRecognizer* recognizer, int toolType, double* distance)
```

**Description**

Obtains the movement distance threshold for gesture recognition for a specific input device type. This API only returns values for device types previously set using **OH_ArkUI_PanGesture_SetDistanceMap**. The default movement distance threshold can be obtained by querying the [UI_INPUT_EVENT_TOOL_TYPE_UNKNOWN](capi-ui-input-event-h.md#anonymous1) type. Other types that have not been set are not returned.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance. |
| int toolType | Tool type for which you want to obtain the threshold. |
| double* distance | Pointer to the movement distance threshold of the gesture recognizer. The unit is px. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Result code.      <br>Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      <br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs.      <br>Returns [ARKUI_ERROR_CODE_RECOGNIZER_TYPE_NOT_SUPPORTED](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the gesture recognizer type is not      supported. |

### OH_ArkUI_SetTouchTestDoneCallback()

```c
ArkUI_ErrorCode OH_ArkUI_SetTouchTestDoneCallback(ArkUI_NodeHandle node, void* userData, void (*touchTestDone)(ArkUI_GestureEvent* event, ArkUI_GestureRecognizerHandleArray recognizers, int32_t count, void* userData))
```

**Description**

Registers a callback that is executed after all gesture recognizers are collected. When the user begins touching the screen, the system performs hit testing and collects gesture recognizers based on the touch location. Subsequently, before processing any move events, the component can use this API to determine the gesture recognizers that will participate in and compete for recognition.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_NodeHandle node | Handle to the node on which the callback is to be set. |
| void\* userData | Pointer to user-defined data. |
| void (\*touchTestDone)(ArkUI_GestureEvent\* event | Callback for completion of gesture recognizer collection. - event: Basic information of the gesture. - recognizers: Array of gesture recognizers. - count: Number of gesture recognizers. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Result code.      <br>Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      <br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_GestureInterrupter_GetUserData()

```c
void* OH_ArkUI_GestureInterrupter_GetUserData(ArkUI_GestureInterruptInfo* event)
```

**Description**

Obtains the custom data from a gesture interruption event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_GestureInterruptInfo](capi-arkui-nativemodule-arkui-gestureinterruptinfo.md)* event | Pointer to the gesture interruption information. |

**Returns**:

| Type | Description |
| -- | -- |
| void* | Pointer to user-defined data. |

### OH_ArkUI_PreventGestureRecognizerBegin()

```c
ArkUI_ErrorCode OH_ArkUI_PreventGestureRecognizerBegin(ArkUI_GestureRecognizer* recognizer)
```

**Description**

Prevents a gesture recognizer from participating in the current gesture recognition before all fingers are lifted. If the system has already determined the result of the gesture recognizer (regardless of success or failure), calling this API will be ineffective.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Result code.      <br>Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      <br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_LongPressGesture_SetAllowableMovement()

```c
ArkUI_ErrorCode OH_ArkUI_LongPressGesture_SetAllowableMovement(ArkUI_GestureRecognizer* recognizer, double allowableMovement)
```

**Description**

Sets the maximum movement distance allowed for gesture recognition by the long press gesture recognizer.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance. |
| double allowableMovement | Maximum movement distance allowed for gesture recognition by the long press gesture recognizer. <br>The unit is px. <br>Value range: (0, +∞). If the value is less than or equal to 0, the default value **15** is used. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Result code.      <br>Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      <br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs.      <br>Returns [ARKUI_ERROR_CODE_RECOGNIZER_TYPE_NOT_SUPPORTED](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the gesture recognizer type is not      supported. |

### OH_ArkUI_GestureCollectInterceptInfo_GetResponseRecognizers()

```c
ArkUI_ErrorCode OH_ArkUI_GestureCollectInterceptInfo_GetResponseRecognizers(const ArkUI_GestureCollectInterceptInfo* info, ArkUI_GestureRecognizerHandleArray* array, int32_t* size)
```

**Description**

Obtains gesture recognizer handles from gesture collection interception information.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| const ArkUI_GestureCollectInterceptInfo* info | Pointer to the gesture collection interception information. |
| ArkUI_GestureRecognizerHandleArray* array | Pointer to the gesture recognizer handle array. |
| int32_t* size | Pointer to the size of the gesture recognizer handle array. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_GestureCollectInterceptInfo_GetTouchRecognizers()

```c
ArkUI_ErrorCode OH_ArkUI_GestureCollectInterceptInfo_GetTouchRecognizers(const ArkUI_GestureCollectInterceptInfo* info, ArkUI_TouchRecognizerHandleArray* recognizers, int32_t* size)
```

**Description**

Obtains touch recognizer handles from gesture collection interception information.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| const ArkUI_GestureCollectInterceptInfo* info | Pointer to the gesture collection interception information. |
| ArkUI_TouchRecognizerHandleArray* recognizers | Pointer to the touch recognizer handle array. |
| int32_t* size | Pointer to the size of the touch recognizer handle array. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_GestureCollectInterceptInfo_SetGestureCollectIntervention()

```c
ArkUI_ErrorCode OH_ArkUI_GestureCollectInterceptInfo_SetGestureCollectIntervention(ArkUI_GestureCollectInterceptInfo* info, OH_ArkUI_GestureCollectIntervention intervention)
```

**Description**

Sets the intervention mode for gesture collection.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_GestureCollectInterceptInfo* info | Pointer to the gesture collection interception information. |
| [OH_ArkUI_GestureCollectIntervention](capi-native-gesture-h.md#oh_arkui_gesturecollectintervention) intervention | Gesture collection intervention mode, which is of the [OH_ArkUI_GestureCollectIntervention](capi-native-gesture-h.md#oh_arkui_gesturecollectintervention) type. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_GetGestureBindNodeUniqueId()

```c
ArkUI_ErrorCode OH_ArkUI_GetGestureBindNodeUniqueId(const ArkUI_GestureRecognizer* recognizer, int32_t* uniqueId)
```

**Description**

Obtains the unique ID of the component bound to a gesture recognizer.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer. |
| int32_t* uniqueId | Pointer to the unique ID of the component bound to the gesture recognizer. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.      <br>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_TouchRecognizer_IsHostBelongsTo()

```c
bool OH_ArkUI_TouchRecognizer_IsHostBelongsTo(const ArkUI_TouchRecognizerHandle recognizer, int32_t uniqueId)
```

**Description**

Checks whether the node bound to the touch recognizer is a descendant node of the passed component.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| const ArkUI_TouchRecognizerHandle recognizer | Touch recognizer handle. |
| int32_t uniqueId | Unique ID of the component. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | true if the node bound to the touch recognizer is a descendant node of the passed component; false      otherwise. |

### OH_ArkUI_GestureRecognizer_IsHostBelongsTo()

```c
bool OH_ArkUI_GestureRecognizer_IsHostBelongsTo(const ArkUI_GestureRecognizer* recognizer, int32_t uniqueId)
```

**Description**

Checks whether the node bound to the gesture recognizer is a descendant node of the passed component.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer. |
| int32_t uniqueId | Unique ID of the component. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | true if the node bound to the gesture recognizer is a descendant node of the passed component; false      otherwise. |


