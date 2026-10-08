# native_gesture.h

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=307c96700aa31ceaed2d16437f8e9e4fabcbd960 translatedAt=2026-08-04T11:13:30.062Z pushedAt=2026-08-05T07:35:18.982Z -->

## Overview

Declares the APIs of **NativeGesture**, supporting capabilities such as gesture recognizers, gesture events, gesture interruption, touch recognizers, gesture collection intervention, and gesture parameter query and setting. It is suitable for scenarios where an application processes gesture recognition, gesture conflicts, and gesture collection intervention through native APIs. The gesture recognition pipeline performs recognition based on priority and competition rules, and gestures can be intercepted through interruption callbacks. The gesture collection intervention mechanism allows dynamic intervention in the gesture collection process during the gesture collection phase.

**File to include**: <arkui/native_gesture.h>

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Structs

| Name                                                                                           | typedef Keyword                      | Description               |
|-----------------------------------------------------------------------------------------------|----------------------------------|-------------------|
| [ArkUI_NativeGestureAPI_1](capi-arkui-nativemodule-arkui-nativegestureapi-1.md) | ArkUI_NativeGestureAPI_1 | Provides APIs for creating tap, long press, swipe, pinch, rotation, and fling gestures as well as gesture groups, and supports binding gestures, removing gestures, and setting gesture interruption callbacks and parallel inner gesture callbacks. This struct is used to configure and manage touch-based interaction recognition and event handling of components. When using this struct to configure gestures, you are advised to follow the workflow: call APIs such as [createTapGesture](capi-arkui-nativemodule-arkui-nativegestureapi-1.md#createtapgesture) to create a gesture recognizer, call [setGestureEventTarget](capi-arkui-nativemodule-arkui-nativegestureapi-1.md#setgestureeventtarget) to register a gesture event callback, and then call [addGestureToNode](capi-arkui-nativemodule-arkui-nativegestureapi-1.md#addgesturetonode) to bind the gesture recognizer to a component node. When the gesture is no longer needed, call [dispose](capi-arkui-nativemodule-arkui-nativegestureapi-1.md#dispose) to release the gesture resource. If you need to unbind the gesture from the node first, call [removeGestureFromNode](capi-arkui-nativemodule-arkui-nativegestureapi-1.md#removegesturefromnode) before calling **dispose()**. For gesture competition scenarios, you can configure the response policy through the gesture priority, blocking mode, or [setGestureInterrupterToNode](capi-arkui-nativemodule-arkui-nativegestureapi-1.md#setgestureinterruptertonode). For scenarios where internal component gestures and external custom gestures need to be recognized in parallel, call [setInnerGestureParallelTo](capi-arkui-nativemodule-arkui-nativegestureapi-1.md#setinnergestureparallelto) to set a parallel inner gesture event callback. |
| [ArkUI_NativeGestureAPI_2](capi-arkui-nativemodule-arkui-nativegestureapi-2.md) | - | Defines a set of gesture APIs, extending [ArkUI_NativeGestureAPI_1](capi-arkui-nativemodule-arkui-nativegestureapi-1.md) with the capability to set a gesture interruption event callback, which is used to continue or interrupt a gesture based on the callback result during gesture recognition. You can access basic gesture APIs through [gestureApi1](capi-arkui-nativemodule-arkui-nativegestureapi-2.md#member-variables) and use [setGestureInterrupterToNode](capi-arkui-nativemodule-arkui-nativegestureapi-2.md#setgestureinterruptertonode) to handle gesture interruption. |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md) | ArkUI_GestureRecognizer | Defines a gesture component instance object, used to represent a gesture recognizer object in ArkUI gesture recognition APIs. After being bound to a UI component, the gesture recognizer listens for touch events and notifies you through a callback when the recognition conditions of the corresponding gesture type are met. Different types of recognizers can be used for gestures such as tap, long press, drag, pinch, rotation, and fling. For detailed mechanisms and usage, see the gesture API description in [native_gesture.h](capi-native-gesture-h.md). |
| [ArkUI_GestureInterruptInfo](capi-arkui-nativemodule-arkui-gestureinterruptinfo.md) | ArkUI_GestureInterruptInfo | Defines a gesture interruption event data type, used to pass information such as the gesture recognizer, response chain gesture recognizer, and touch recognizer to the gesture interruption callback. The callback can return a continuation or rejection result based on the information. For the gesture interruption mechanism and APIs, see the gesture interruption API description in [native_gesture.h](capi-native-gesture-h.md). |
| [ArkUI_GestureEvent](capi-arkui-nativemodule-arkui-gestureevent.md)                           | ArkUI_GestureEvent               | Defines a gesture event data type object, used to carry and pass gesture event-related data during gesture event processing. This struct supports obtaining key information such as the gesture event type, coordinates, and timestamp. It is applicable to scenarios that require handling touch gesture interactions, such as tap, long press, drag, and pinch gesture recognition and response. You can obtain event information through related gesture event APIs. |
| [ArkUI_GestureEventTargetInfo](capi-arkui-nativemodule-arkui-gestureeventtargetinfo.md) | ArkUI_GestureEventTargetInfo | Defines target information type of a gesture event, used to query the scroll start, scroll end, and other states of the gesture event target object during gesture processing. It is mainly applicable to scrollable container components. You can obtain this object from the gesture recognizer through [OH_ArkUI_GetGestureEventTargetInfo](capi-native-gesture-h.md#oh_arkui_getgestureeventtargetinfo) and read the target state through target information query APIs. |
| [ArkUI_ParallelInnerGestureEvent](capi-arkui-nativemodule-arkui-parallelinnergestureevent.md) | ArkUI_ParallelInnerGestureEvent | Defines a parallel inner gesture event. This struct is passed as a parameter to the [setInnerGestureParallelTo](capi-arkui-nativemodule-arkui-nativegestureapi-1.md#setinnergestureparallelto) callback, containing the current built-in gesture recognizer, conflicting gesture recognizers in the response chain, and user-defined data, for the callback to select the object that needs to be recognized in parallel with the current built-in gesture. |
| [ArkUI_TouchRecognizer](capi-arkui-nativemodule-arkui-touchrecognizer.md) | ArkUI_TouchRecognizer | Defines a touch recognizer. The touch recognizer is used to represent the touch event processing object returned in gesture interruption or gesture collection interception information. You can obtain its node handle or cancel touch events through related APIs. For specific APIs, see [native_gesture.h](capi-native-gesture-h.md). |
| [ArkUI_TouchRecognizer*](capi-arkui-nativemodule-arkui-touchrecognizerhandle.md) | ArkUI_TouchRecognizerHandle | Defines a touch recognizer handle, used to represent a touch recognizer object and pass it in APIs such as gesture interruption and gesture collection interception. For specific APIs, see [native_gesture.h](capi-native-gesture-h.md). |
| [ArkUI_TouchRecognizerHandle*](capi-arkui-nativemodule-arkui-touchrecognizerhandlearray.md)   | ArkUI_TouchRecognizerHandleArray | Defines a touch recognizer handle array, used for batch management of multiple touch recognizers, for example, obtaining multiple touch recognizer handles from gesture interruption information. |
| [ArkUI_GestureRecognizer*](capi-arkui-nativemodule-arkui-gesturerecognizerhandle.md) | ArkUI_GestureRecognizerHandle | Defines a gesture recognizer handle type, which is an alias wrapper of the **ArkUI_GestureRecognizer** pointer type, used to represent a gesture recognizer object in ArkUI native gesture APIs. This handle can be used as an object reference in scenarios such as gesture recognizer creation, attribute configuration, and event callback listening, facilitating unified transfer, management, and operations of gesture recognizers at the native layer. For how to obtain and use the APIs, see [native_gesture.h](capi-native-gesture-h.md). |
| [ArkUI_GestureRecognizerHandle*](capi-arkui-nativemodule-arkui-gesturerecognizerhandlearray.md) | ArkUI_GestureRecognizerHandleArray | Defines a gesture recognizer handle array type, used to represent or pass multiple gesture recognizer handles, for example, obtaining the set of gesture recognizers in the response chain. For detailed mechanisms and usage, see the gesture API description in [native_gesture.h](capi-native-gesture-h.md). |
| [ArkUI_NativeGestureAPI_3](capi-arkui-nativemodule-arkui-nativegestureapi-3.md) | ArkUI_NativeGestureAPI_3 | Defines a set of gesture APIs, including the gesture APIs from the [ArkUI_NativeGestureAPI_1](capi-arkui-nativemodule-arkui-nativegestureapi-1.md) and [ArkUI_NativeGestureAPI_2](capi-arkui-nativemodule-arkui-nativegestureapi-2.md) structs as well as newly added gesture APIs. This API set supports setting parallel gesture event callbacks for ArkUI nodes. The callbacks can select the objects that need to be recognized in parallel with the current gesture from the conflicting gesture recognizers in the response chain. For related event data, see [ArkUI_ParallelGestureEvent](capi-arkui-nativemodule-arkui-parallelgestureevent.md). |
| [ArkUI_ParallelGestureEvent](capi-arkui-nativemodule-arkui-parallelgestureevent.md) | ArkUI_ParallelGestureEvent | Defines a parallel gesture event. This struct is passed as a parameter to the [setGestureParallelTo](capi-arkui-nativemodule-arkui-nativegestureapi-3.md#setgestureparallelto) callback, containing the current gesture recognizer, conflicting gesture recognizers in the response chain, and user-defined data, for the callback to select the object that needs to be recognized in parallel with the current gesture. |

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ArkUI_GestureEventActionType](#arkui_gestureeventactiontype) | ArkUI_GestureEventActionType | Enumerates gesture event types.|
| [ArkUI_GesturePriority](#arkui_gesturepriority) | ArkUI_GesturePriority | Enumerates gesture priorities. **NORMAL** applies to default gesture recognition scenarios; **PRIORITY** applies to scenarios where a specific gesture needs to be prioritized (for example, prioritizing a tap over a swipe); **PARALLEL** applies to scenarios where multiple gestures need to respond independently and simultaneously (for example, recognizing pinch and rotation at the same time). |
| [ArkUI_GroupGestureMode](#arkui_groupgesturemode) | ArkUI_GroupGestureMode | Enumerates gesture group modes. **SEQUENTIAL_GROUP** applies to scenarios where gestures need to be recognized step by step (for example, long press followed by swipe); **PARALLEL_GROUP** applies to scenarios where multiple gestures need to be recognized independently and simultaneously (for example, listening for pinch and rotation at the same time); **EXCLUSIVE_GROUP** applies to scenarios where multiple gestures compete exclusively and only one needs to succeed (for example, swipe and long press being mutually exclusive). |
| [ArkUI_GestureDirection](#arkui_gesturedirection) | ArkUI_GestureDirection | Enumerates gesture directions.|
| [ArkUI_GestureMask](#arkui_gesturemask) | ArkUI_GestureMask | Enumerates gesture masking modes. **NORMAL_GESTURE_MASK** applies to default scenarios, where child component gestures are recognized in the normal order; **IGNORE_INTERNAL_GESTURE_MASK** applies to scenarios where the parent component needs exclusive gesture control (for example, blocking gesture interference from child components during full-screen swiping), and it masks child component gestures, including system built-in gestures. |
| [ArkUI_GestureRecognizerType](#arkui_gesturerecognizertype) | ArkUI_GestureRecognizerType | Enumerates gesture recognizer types.|
| [ArkUI_GestureInterruptResult](#arkui_gestureinterruptresult) | ArkUI_GestureInterruptResult | Enumerates gesture interruption results.|
| [ArkUI_GestureRecognizerState](#arkui_gesturerecognizerstate) | ArkUI_GestureRecognizerState | Enumerates the gesture recognizer states.|
| [OH_ArkUI_GestureCollectIntervention](#oh_arkui_gesturecollectintervention) | OH_ArkUI_GestureCollectIntervention | Defines the intervention types for gesture and event collection.<br>**Since**: 26.0.0|

### Functions

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [typedef void (\*ArkUI_GestureRecognizerDisposeNotifyCallback)(ArkUI_GestureRecognizer* recognizer, void* userData)](#arkui_gesturerecognizerdisposenotifycallback) | ArkUI_GestureRecognizerDisposeNotifyCallback | Defines a callback function for notifying gesture recognizer destruction.|
| [bool OH_ArkUI_GestureInterruptInfo_GetSystemFlag(const ArkUI_GestureInterruptInfo* event)](#oh_arkui_gestureinterruptinfo_getsystemflag) | - | Checks whether a gesture is a system built-in gesture.|
| [ArkUI_GestureRecognizer* OH_ArkUI_GestureInterruptInfo_GetRecognizer(const ArkUI_GestureInterruptInfo* event)](#oh_arkui_gestureinterruptinfo_getrecognizer) | - | Obtains the pointer to the interrupted gesture recognizer.|
| [ArkUI_GestureEvent* OH_ArkUI_GestureInterruptInfo_GetGestureEvent(const ArkUI_GestureInterruptInfo* event)](#oh_arkui_gestureinterruptinfo_getgestureevent) | - | Obtains the pointer to the interrupted gesture event.|
| [int32_t OH_ArkUI_GestureInterruptInfo_GetSystemRecognizerType(const ArkUI_GestureInterruptInfo* event)](#oh_arkui_gestureinterruptinfo_getsystemrecognizertype) | - | Obtains the type of the system built-in gesture to trigger.|
| [int32_t OH_ArkUI_GestureInterruptInfo_GetTouchRecognizers(const ArkUI_GestureInterruptInfo* info,ArkUI_TouchRecognizerHandleArray* recognizers, int32_t* size)](#oh_arkui_gestureinterruptinfo_gettouchrecognizers) | - | Obtains touch recognizers from gesture interruption information.|
| [ArkUI_NodeHandle OH_ArkUI_TouchRecognizer_GetNodeHandle(const ArkUI_TouchRecognizerHandle recognizer)](#oh_arkui_touchrecognizer_getnodehandle) | - | Obtains the component handle corresponding to a touch recognizer.|
| [int32_t OH_ArkUI_TouchRecognizer_CancelTouch(ArkUI_TouchRecognizerHandle recognizer, ArkUI_GestureInterruptInfo* info)](#oh_arkui_touchrecognizer_canceltouch) | - | Sends a cancel touch event to a touch recognizer in a gesture interruption callback. This API is applicable to scenarios such as nested scrolling, where the parent component needs to take over scroll control. You can use this API to cancel the touch event of the child component's touch recognizer to avoid gesture conflicts. |
| [ArkUI_GestureEventActionType OH_ArkUI_GestureEvent_GetActionType(const ArkUI_GestureEvent* event)](#oh_arkui_gestureevent_getactiontype) | - | Obtains the gesture event type.|
| [const ArkUI_UIInputEvent* OH_ArkUI_GestureEvent_GetRawInputEvent(const ArkUI_GestureEvent* event)](#oh_arkui_gestureevent_getrawinputevent) | - | Obtains the raw input event of the gesture.|
| [int32_t OH_ArkUI_LongPress_GetRepeatCount(const ArkUI_GestureEvent* event)](#oh_arkui_longpress_getrepeatcount) | - | Checks whether the event is a repeated trigger event.|
| [float OH_ArkUI_PanGesture_GetVelocity(const ArkUI_GestureEvent* event)](#oh_arkui_pangesture_getvelocity) | - | Obtains the velocity of a pan gesture along the main axis.|
| [float OH_ArkUI_PanGesture_GetVelocityX(const ArkUI_GestureEvent* event)](#oh_arkui_pangesture_getvelocityx) | - | Obtains the velocity of a pan gesture along the x-axis.|
| [float OH_ArkUI_PanGesture_GetVelocityY(const ArkUI_GestureEvent* event)](#oh_arkui_pangesture_getvelocityy) | - | Obtains the velocity of a pan gesture along the y-axis.|
| [float OH_ArkUI_PanGesture_GetOffsetX(const ArkUI_GestureEvent* event)](#oh_arkui_pangesture_getoffsetx) | - | Obtains the relative offset of a pan gesture along the x-axis.|
| [float OH_ArkUI_PanGesture_GetOffsetY(const ArkUI_GestureEvent* event)](#oh_arkui_pangesture_getoffsety) | - | Obtains the relative offset of a pan gesture along the y-axis.|
| [float OH_ArkUI_SwipeGesture_GetAngle(const ArkUI_GestureEvent* event)](#oh_arkui_swipegesture_getangle) | - | Obtains the angle information of the swipe gesture, that is, the angle between the instantaneous direction of the finger swipe and the positive horizontal direction. Based on the positive horizontal direction, if the swipe direction is on the clockwise side of the positive horizontal direction, the angle ranges from 0 to 180 degrees; if the swipe direction is on the counterclockwise side of the positive horizontal direction, the angle ranges from 0 to –180 degrees.|
| [float OH_ArkUI_SwipeGesture_GetVelocity(const ArkUI_GestureEvent* event)](#oh_arkui_swipegesture_getvelocity) | - | Obtains the average velocity of all fingers used in the swipe gesture.|
| [float OH_ArkUI_RotationGesture_GetAngle(const ArkUI_GestureEvent* event)](#oh_arkui_rotationgesture_getangle) | - | Obtains the angle information of a rotation gesture.|
| [float OH_ArkUI_PinchGesture_GetScale(const ArkUI_GestureEvent* event)](#oh_arkui_pinchgesture_getscale) | - | Obtains the scale ratio of a pinch gesture.|
| [float OH_ArkUI_PinchGesture_GetCenterX(const ArkUI_GestureEvent* event)](#oh_arkui_pinchgesture_getcenterx) | - | Obtains the x-coordinate of the center of the pinch gesture, relative to the upper left corner of the current component.|
| [float OH_ArkUI_PinchGesture_GetCenterY(const ArkUI_GestureEvent* event)](#oh_arkui_pinchgesture_getcentery) | - | Obtains the y-coordinate of the center of the pinch gesture, relative to the upper left corner of the current component.|
| [ArkUI_NodeHandle OH_ArkUI_GestureEvent_GetNode(const ArkUI_GestureEvent* event)](#oh_arkui_gestureevent_getnode) | - | Obtains the ArkUI component to which the gesture is bound.|
| [int32_t OH_ArkUI_GetResponseRecognizersFromInterruptInfo(const ArkUI_GestureInterruptInfo* event,ArkUI_GestureRecognizerHandleArray* responseChain, int32_t* count)](#oh_arkui_getresponserecognizersfrominterruptinfo) | - | Obtains information about a gesture response chain.|
| [int32_t OH_ArkUI_SetGestureRecognizerEnabled(ArkUI_GestureRecognizer* recognizer, bool enabled)](#oh_arkui_setgesturerecognizerenabled) | - | Sets the enabled state of a gesture recognizer. This API is applicable to scenarios where gesture recognition needs to be dynamically enabled or disabled based on the application's interaction state, for example, disabling the swipe gesture during page scrolling animation to avoid accidental touches, or disabling the drag gesture in editing mode. |
| [int32_t OH_ArkUI_SetGestureRecognizerLimitFingerCount(ArkUI_GestureRecognizer* recognizer, bool limitFingerCount)](#oh_arkui_setgesturerecognizerlimitfingercount) | - | Sets whether to enable strict finger count checking. If this feature is enabled and the actual number of touch fingers does not match the set number, the gesture recognition fails.|
| [bool OH_ArkUI_GetGestureRecognizerEnabled(ArkUI_GestureRecognizer* recognizer)](#oh_arkui_getgesturerecognizerenabled) | - | Obtains the enabled state of a gesture recognizer.|
| [int32_t OH_ArkUI_GetGestureRecognizerState(ArkUI_GestureRecognizer* recognizer, ArkUI_GestureRecognizerState* state)](#oh_arkui_getgesturerecognizerstate) | - | Obtains the state of a gesture recognizer.|
| [int32_t OH_ArkUI_GetGestureEventTargetInfo(ArkUI_GestureRecognizer* recognizer, ArkUI_GestureEventTargetInfo** info)](#oh_arkui_getgestureeventtargetinfo) | - | Obtains the information about a gesture event target.|
| [int32_t OH_ArkUI_GestureEventTargetInfo_IsScrollBegin(ArkUI_GestureEventTargetInfo* info, bool* ret)](#oh_arkui_gestureeventtargetinfo_isscrollbegin) | - | Obtains whether this scrollable container component is scrolled to the top.|
| [int32_t OH_ArkUI_GestureEventTargetInfo_IsScrollEnd(ArkUI_GestureEventTargetInfo* info, bool* ret)](#oh_arkui_gestureeventtargetinfo_isscrollend) | - | Obtains whether this scrollable container component is scrolled to the bottom.|
| [int32_t OH_ArkUI_GetPanGestureDirectionMask(ArkUI_GestureRecognizer* recognizer,ArkUI_GestureDirectionMask* directionMask)](#oh_arkui_getpangesturedirectionmask) | - | Obtains the direction of a pan gesture. It is recommended to use **OH_ArkUI_GetGestureParam_DirectMask** (API version 18) first, which is a unified parameter query API. **OH_ArkUI_GetPanGestureDirectionMask** is an earlier API (API version 12) with the same functionality as **OH_ArkUI_GetGestureParam_DirectMask**. |
| [bool OH_ArkUI_IsBuiltInGesture(ArkUI_GestureRecognizer* recognizer)](#oh_arkui_isbuiltingesture) | - | Obtains whether a gesture is a built-in gesture.|
| [int32_t OH_ArkUI_GetGestureTag(ArkUI_GestureRecognizer* recognizer, char* buffer, int32_t bufferSize, int32_t* result)](#oh_arkui_getgesturetag) | - | Obtains the tag of a gesture recognizer.|
| [int32_t OH_ArkUI_GetGestureBindNodeId(ArkUI_GestureRecognizer* recognizer, char* nodeId, int32_t size,int32_t* result)](#oh_arkui_getgesturebindnodeid) | - | Obtains the ID of the component bound to a gesture recognizer (in string format, that is, the value of the **nodeId** attribute you set on the ArkUI component). To obtain the system-assigned unique identifier in integer format, use **OH_ArkUI_GetGestureBindNodeUniqueId**. |
| [bool OH_ArkUI_IsGestureRecognizerValid(ArkUI_GestureRecognizer* recognizer)](#oh_arkui_isgesturerecognizervalid) | - | Obtains whether a gesture recognizer is valid.|
| [void* OH_ArkUI_ParallelInnerGestureEvent_GetUserData(ArkUI_ParallelInnerGestureEvent* event)](#oh_arkui_parallelinnergestureevent_getuserdata) | - | Obtains custom data in the parallel built-in gesture event.|
| [ArkUI_GestureRecognizer* OH_ArkUI_ParallelInnerGestureEvent_GetCurrentRecognizer(ArkUI_ParallelInnerGestureEvent* event)](#oh_arkui_parallelinnergestureevent_getcurrentrecognizer) | - | Obtains the current gesture recognizer in a parallel built-in gesture event.|
| [int32_t OH_ArkUI_ParallelInnerGestureEvent_GetConflictRecognizers(ArkUI_ParallelInnerGestureEvent* event,ArkUI_GestureRecognizerHandleArray* array, int32_t* size)](#oh_arkui_parallelinnergestureevent_getconflictrecognizers) | - | Obtains the conflicting gesture recognizers in a parallel built-in gesture event.|
| [int32_t OH_ArkUI_SetArkUIGestureRecognizerDisposeNotify(ArkUI_GestureRecognizer* recognizer,ArkUI_GestureRecognizerDisposeNotifyCallback callback, void* userData)](#oh_arkui_setarkuigesturerecognizerdisposenotify) | - | Sets a callback function for notifying gesture recognizer destruction. This API is applicable to scenarios where resource cleanup or state update is required when the gesture recognizer is disposed of, for example, releasing custom data associated with the gesture recognizer or removing references to other objects. |
| [int32_t OH_ArkUI_GetGestureParam_DirectMask(ArkUI_GestureRecognizer* recognizer, ArkUI_GestureDirectionMask* directMask)](#oh_arkui_getgestureparam_directmask) | - | Obtains the swipe direction of a gesture recognizer.|
| [int32_t OH_ArkUI_GetGestureParam_FingerCount(ArkUI_GestureRecognizer* recognizer, int* finger)](#oh_arkui_getgestureparam_fingercount) | - | Obtains the number of fingers used by a gesture recognizer.|
| [int32_t OH_ArkUI_GetGestureParam_limitFingerCount(ArkUI_GestureRecognizer* recognizer, bool* isLimited)](#oh_arkui_getgestureparam_limitfingercount) | - | Checks whether a gesture recognizer has a finger count limit.|
| [int32_t OH_ArkUI_GetGestureParam_repeat(ArkUI_GestureRecognizer* recognizer, bool* isRepeat)](#oh_arkui_getgestureparam_repeat) | - | Checks whether a gesture recognizer continuously triggers event callbacks.|
| [int32_t OH_ArkUI_GetGestureParam_distance(ArkUI_GestureRecognizer* recognizer, double* distance)](#oh_arkui_getgestureparam_distance) | - | Obtains the allowed movement distance range for a gesture recognizer.|
| [int32_t OH_ArkUI_GetGestureParam_speed(ArkUI_GestureRecognizer* recognizer, double* speed)](#oh_arkui_getgestureparam_speed) | - | Obtains the minimum swipe speed recognized by a gesture recognizer.|
| [int32_t OH_ArkUI_GetGestureParam_duration(ArkUI_GestureRecognizer* recognizer, int* duration)](#oh_arkui_getgestureparam_duration) | - | Obtains the minimum duration required to trigger a long press by a gesture recognizer.|
| [int32_t OH_ArkUI_GetGestureParam_angle(ArkUI_GestureRecognizer* recognizer, double* angle)](#oh_arkui_getgestureparam_angle) | - | Obtains the minimum angle change required for a rotation gesture to be recognized by a gesture recognizer.|
| [int32_t OH_ArkUI_GetGestureParam_distanceThreshold(ArkUI_GestureRecognizer* recognizer, double* distanceThreshold)](#oh_arkui_getgestureparam_distancethreshold) | - | Obtains the movement threshold distance for gesture recognition.|
| [ArkUI_ErrorCode OH_ArkUI_PanGesture_SetDistanceMap(ArkUI_GestureRecognizer* recognizer, int size, int* toolTypeArray, double* distanceArray)](#oh_arkui_pangesture_setdistancemap) | - | Sets the minimum sliding distance threshold mapping for gesture recognition.|
| [ArkUI_ErrorCode OH_ArkUI_PanGesture_GetDistanceByToolType(ArkUI_GestureRecognizer* recognizer, int toolType, double* distance)](#oh_arkui_pangesture_getdistancebytooltype) | - | Obtains the movement distance threshold for gesture recognition for a specific input device type. This API only returns values for device types previously set using **OH_ArkUI_PanGesture_SetDistanceMap**. The default pan gesture activation threshold can be obtained using **UI_INPUT_EVENT_TOOL_TYPE_UNKNOWN**. This API returns no value for unconfigured device types.|
| [ArkUI_ErrorCode OH_ArkUI_SetTouchTestDoneCallback(ArkUI_NodeHandle node,void* userData,void (\*touchTestDone)(ArkUI_GestureEvent* event,ArkUI_GestureRecognizerHandleArray recognizers,int32_t count,void* userData))](#oh_arkui_settouchtestdonecallback) | - | Registers a callback that is executed after all gesture recognizers are collected. When the user begins touching the screen, the system performs hit testing and collects gesture recognizers based on the touch location. Subsequently, before processing any move events, the component can use this API to determine the gesture recognizers that will participate in and compete for recognition.|
| [void* OH_ArkUI_GestureInterrupter_GetUserData(ArkUI_GestureInterruptInfo* event)](#oh_arkui_gestureinterrupter_getuserdata) | - | Obtains the custom data from a gesture interruption event.|
| [ArkUI_ErrorCode OH_ArkUI_PreventGestureRecognizerBegin(ArkUI_GestureRecognizer* recognizer)](#oh_arkui_preventgesturerecognizerbegin) | - | Prevents a gesture recognizer from participating in the current gesture recognition before all fingers are lifted. This API is applicable to scenarios where a specified gesture recognizer needs to be dynamically excluded during gesture competition. If the system has already determined the result of the gesture recognizer (regardless of success or failure), calling this API will be ineffective. |
| [ArkUI_ErrorCode OH_ArkUI_LongPressGesture_SetAllowableMovement(ArkUI_GestureRecognizer* recognizer, double allowableMovement)](#oh_arkui_longpressgesture_setallowablemovement) | - | Sets the maximum movement distance allowed for gesture recognition by the long press gesture recognizer.|
| [ArkUI_ErrorCode OH_ArkUI_LongPressGesture_GetAllowableMovement(ArkUI_GestureRecognizer* recognizer, double* allowableMovement)](#oh_arkui_longpressgesture_getallowablemovement) | - | Obtains the maximum movement distance allowed for gesture recognition by the long press gesture recognizer.|
| [ArkUI_ErrorCode OH_ArkUI_GestureCollectInterceptInfo_GetResponseRecognizers(const ArkUI_GestureCollectInterceptInfo* info, ArkUI_GestureRecognizerHandleArray* array, int32_t* size)](#oh_arkui_gesturecollectinterceptinfo_getresponserecognizers) | - | Obtains gesture recognizer handles from gesture collection interception information.<br>**Since**: 26.0.0|
| [ArkUI_ErrorCode OH_ArkUI_GestureCollectInterceptInfo_GetTouchRecognizers(const ArkUI_GestureCollectInterceptInfo* info, ArkUI_TouchRecognizerHandleArray* recognizers, int32_t* size)](#oh_arkui_gesturecollectinterceptinfo_gettouchrecognizers) | - | Obtains touch recognizer handles from gesture collection interception information.<br>**Since**: 26.0.0|
| [ArkUI_ErrorCode OH_ArkUI_GestureCollectInterceptInfo_SetGestureCollectIntervention(ArkUI_GestureCollectInterceptInfo* info, OH_ArkUI_GestureCollectIntervention intervention)](#oh_arkui_gesturecollectinterceptinfo_setgesturecollectintervention) | - | Sets the intervention mode for gesture collection.<br>**Since**: 26.0.0|
| [ArkUI_ErrorCode OH_ArkUI_GetGestureBindNodeUniqueId(const ArkUI_GestureRecognizer* recognizer, int32_t* uniqueId)](#oh_arkui_getgesturebindnodeuniqueid) | - | Obtains the unique ID of the component bound to a gesture recognizer.<br>**Since**: 26.0.0|
| [bool OH_ArkUI_TouchRecognizer_IsHostBelongsTo(const ArkUI_TouchRecognizerHandle recognizer, int32_t uniqueId)](#oh_arkui_touchrecognizer_ishostbelongsto) | - | Checks whether the node bound to the touch recognizer is a descendant node of the passed component.<br>**Since**: 26.0.0|
| [bool OH_ArkUI_GestureRecognizer_IsHostBelongsTo(const ArkUI_GestureRecognizer* recognizer, int32_t uniqueId)](#oh_arkui_gesturerecognizer_ishostbelongsto) | - | Checks whether the node bound to the gesture recognizer is a descendant node of the passed component.<br>**Since**: 26.0.0|

### Variables

| Name      | typedef Keyword                | Description                                                                                                                                   |
|----------|----------------------------|---------------------------------------------------------------------------------------------------------------------------------------|
| uint32_t | ArkUI_GestureDirectionMask | Defines a set of gesture directions.<br>Example: ArkUI_GestureDirectionMask directions = GESTURE_DIRECTION_LEFT \| GESTURE_DIRECTION_RIGHT<br>This example indicates that the leftward and rightward directions are supported.|
| uint32_t | ArkUI_GestureEventActionTypeMask   | Defines a set of gesture event types. Example: ArkUI_GestureEventActionTypeMask actions = GESTURE_EVENT_ACTION_ACCEPT \| GESTURE_EVENT_ACTION_UPDATE                  |

### Example

| Name|  Description|
| -- | -- |
| <!--RP1-->[NdkGestureSetting](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NdkGestureSetting)<!--RP1End--> | Examples demonstrating gesture binding, gesture removal, and custom gesture detection are added since API version 20.|
| <!--RP2-->[NdkGestureNestScroll](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NdkGestureNestScroll)<!--RP2End--> | Examples demonstrating nested scrolling through gesture APIs are added since API version 20.|
| <!--RP3-->[NdkGestureBlocking](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NdkGestureBlocking)<!--RP3End--> | Examples demonstrating gesture interception are added since API version 20.|

## Enum Description

### ArkUI_GestureEventActionType

```c
enum ArkUI_GestureEventActionType
```

**Description**

Enumerates gesture event types.

**Since**: 12

| Value| Description|
| -- | -- |
| GESTURE_EVENT_ACTION_ACCEPT = 0x01 | Triggered.|
| GESTURE_EVENT_ACTION_UPDATE = 0x02 | Updated.|
| GESTURE_EVENT_ACTION_END = 0x04 | Ended.|
| GESTURE_EVENT_ACTION_CANCEL = 0x08 | Canceled.|

### ArkUI_GesturePriority

```c
enum ArkUI_GesturePriority
```

**Description**

Enumerates gesture priorities. **NORMAL** applies to default gesture recognition scenarios; **PRIORITY** applies to scenarios where a specific gesture needs to be prioritized (for example, prioritizing a tap over a swipe); **PARALLEL** applies to scenarios where multiple gestures need to respond independently and simultaneously (for example, recognizing pinch and rotation at the same time).

**Since**: 12

| Value| Description|
| -- | -- |
| NORMAL = 0 | Normal.|
| PRIORITY = 1 | High priority.|
| PARALLEL = 2 | Parallel.|

### ArkUI_GroupGestureMode

```c
enum ArkUI_GroupGestureMode
```

**Description**

Enumerates gesture group modes. **SEQUENTIAL_GROUP** applies to scenarios where gestures need to be recognized step by step (for example, long press followed by swipe); **PARALLEL_GROUP** applies to scenarios where multiple gestures need to be recognized independently and simultaneously (for example, listening for pinch and rotation at the same time); **EXCLUSIVE_GROUP** applies to scenarios where multiple gestures compete exclusively and only one needs to succeed (for example, swipe and long press being mutually exclusive).

**Since**: 12

| Value| Description|
| -- | -- |
| SEQUENTIAL_GROUP = 0 | Sequential recognition. Gestures are recognized in the registration sequence until all gestures are recognized successfully. Once one gesture fails to be recognized, all subsequent gestures fail to be recognized. Only the last gesture in the gesture group can respond to the end event.|
| PARALLEL_GROUP = 1 | Parallel recognition. Registered gestures are recognized concurrently until all gestures are recognized. The recognition result of each gesture does not affect each other.|
| EXCLUSIVE_GROUP = 2 | Exclusive recognition. Registered gestures are identified concurrently. If one gesture is successfully recognized, gesture recognition ends.|

### ArkUI_GestureDirection

```c
enum ArkUI_GestureDirection
```

**Description**

Enumerates gesture directions.

**Since**: 12

| Value| Description|
| -- | -- |
| GESTURE_DIRECTION_ALL = 0b1111 | All directions.|
| GESTURE_DIRECTION_HORIZONTAL = 0b0011 | Horizontal direction.|
| GESTURE_DIRECTION_VERTICAL = 0b1100 | Vertical direction.|
| GESTURE_DIRECTION_LEFT = 0b0001 | Leftward.|
| GESTURE_DIRECTION_RIGHT = 0b0010 | Rightward.|
| GESTURE_DIRECTION_UP = 0b0100 | Upward.|
| GESTURE_DIRECTION_DOWN = 0b1000 | Downward.|
| GESTURE_DIRECTION_NONE = 0 | None.|

### ArkUI_GestureMask

```c
enum ArkUI_GestureMask
```

**Description**

Enumerates gesture masking modes. **NORMAL_GESTURE_MASK** applies to default scenarios, where child component gestures are recognized in the normal order; **IGNORE_INTERNAL_GESTURE_MASK** applies to scenarios where the parent component needs exclusive gesture control (for example, blocking gesture interference from child components during full-screen swiping), and it masks child component gestures, including system built-in gestures.

**Since**: 12

| Value| Description|
| -- | -- |
| NORMAL_GESTURE_MASK = 0 | The gestures of child components are enabled and recognized based on the default gesture recognition sequence.|
| IGNORE_INTERNAL_GESTURE_MASK = 1 | The gestures of child components are disabled, including the built-in gestures.|

### ArkUI_GestureRecognizerType

```c
enum ArkUI_GestureRecognizerType
```

**Description**

Enumerates gesture recognizer types.

**Since**: 12

| Value| Description                               |
| -- |-----------------------------------|
| TAP_GESTURE = 0 | Tap.                            |
| LONG_PRESS_GESTURE = 1 | Long press.                            |
| PAN_GESTURE = 2 | Pan.                            |
| PINCH_GESTURE = 3 | Pinch.                            |
| ROTATION_GESTURE = 4 | Rotate.                            |
| SWIPE_GESTURE = 5 | Swipe.                            |
| GROUP_GESTURE = 6 | A group of gestures.                            |
| CLICK_GESTURE = 7 | Click gesture registered with **onClick**.<br>**Since**: 20|
| DRAG_DROP = 8 | Drag-and-drop gesture.<br>**Since**: 20       |

### OH_ArkUI_GestureCollectIntervention

```c
enum OH_ArkUI_GestureCollectIntervention
```

**Description**

Defines the intervention types for gesture and event collection.

**Since**: 26.0.0

| Value| Description|
| -- | -- |
| OH_ARKUI_GESTURE_COLLECT_INTERVENTION_CONTINUE = 0 | Continues the normal gesture and event collection flow. No intervention is performed.|
| OH_ARKUI_GESTURE_COLLECT_INTERVENTION_DISCARD_LOWER = 1 | Discards all low-priority gestures and events to be collected.<br>The gestures of the left sibling node and ancestor nodes (parent nodes and above) are discarded.<br>Only the gestures already collected on the current node and higher-priority nodes are retained. |
| OH_ARKUI_GESTURE_COLLECT_INTERVENTION_DISCARD_HIGHER = 2 | Discards all collected high-priority gestures and events.<br>The gestures of the right sibling node and the current node are discarded.<br>Continues processing the collection flow for lower-priority gestures (left sibling and ancestor nodes). |
| OH_ARKUI_GESTURE_COLLECT_INTERVENTION_DISCARD_SELF = 3 | Discards the gestures and events of the current node.<br>The gestures and events of the current node are excluded from the gesture tree.<br>The gestures of the sibling nodes (left and right) and the ancestor nodes are still collected. |
| OH_ARKUI_GESTURE_COLLECT_INTERVENTION_DISCARD_LOWER_PRIORITY_SIBLINGS = 4 | Discards the gestures and events to be collected from the left sibling node.<br>The gestures and events of the current node and the collected gestures and events of the right sibling node are retained.<br>Continues processing the collection flow for the parent and ancestor nodes. |

### ArkUI_GestureInterruptResult

```c
enum ArkUI_GestureInterruptResult
```

**Description**

Enumerates gesture interruption results.

**Since**: 12

| Value| Description|
| -- | -- |
| GESTURE_INTERRUPT_RESULT_CONTINUE = 0 | The gesture recognition process continues.|
| GESTURE_INTERRUPT_RESULT_REJECT = 1 | The gesture recognition process is paused.|

### ArkUI_GestureRecognizerState

```c
enum ArkUI_GestureRecognizerState
```

**Description**

Enumerates the gesture recognizer states.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_GESTURE_RECOGNIZER_STATE_READY = 0 | Ready.|
| ARKUI_GESTURE_RECOGNIZER_STATE_DETECTING = 1 | Detecting.|
| ARKUI_GESTURE_RECOGNIZER_STATE_PENDING = 2 | Pending.|
| ARKUI_GESTURE_RECOGNIZER_STATE_BLOCKED = 3 | Blocked.|
| ARKUI_GESTURE_RECOGNIZER_STATE_SUCCESSFUL = 4 | Successful.|
| ARKUI_GESTURE_RECOGNIZER_STATE_FAILED = 5 | Failed.|

## Function Description

### ArkUI_GestureRecognizerDisposeNotifyCallback()

```c
typedef void (*ArkUI_GestureRecognizerDisposeNotifyCallback)(ArkUI_GestureRecognizer* recognizer, void* userData)
```

**Description**

Defines a callback function for notifying gesture recognizer destruction.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance.|
| void* userData | Pointer to user-defined data.|

### OH_ArkUI_GestureInterruptInfo_GetSystemFlag()

```c
bool OH_ArkUI_GestureInterruptInfo_GetSystemFlag(const ArkUI_GestureInterruptInfo* event)
```

**Description**

Checks whether a gesture is a system built-in gesture.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_GestureInterruptInfo](capi-arkui-nativemodule-arkui-gestureinterruptinfo.md)* event | Pointer to the gesture interruption callback event.|

**Returns**

| Type| Description|
| -- | -- |
| bool | **true**: built-in gesture.<br>         **false**: non-built-in gesture.|

### OH_ArkUI_GestureInterruptInfo_GetRecognizer()

```c
ArkUI_GestureRecognizer* OH_ArkUI_GestureInterruptInfo_GetRecognizer(const ArkUI_GestureInterruptInfo* event)
```

**Description**

Obtains the pointer to the interrupted gesture recognizer.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_GestureInterruptInfo](capi-arkui-nativemodule-arkui-gestureinterruptinfo.md)* event | Pointer to the gesture interruption callback event.|

**Returns**

| Type                          | Description|
|------------------------------| -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* | Pointer to the interrupted gesture recognizer.|

### OH_ArkUI_GestureInterruptInfo_GetGestureEvent()

```c
ArkUI_GestureEvent* OH_ArkUI_GestureInterruptInfo_GetGestureEvent(const ArkUI_GestureInterruptInfo* event)
```

**Description**

Obtains the pointer to the interrupted gesture event.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_GestureInterruptInfo](capi-arkui-nativemodule-arkui-gestureinterruptinfo.md)* event | Pointer to the gesture interruption callback event.|

**Returns**

| Type                     | Description|
|-------------------------| -- |
| [ArkUI_GestureEvent](capi-arkui-nativemodule-arkui-gestureevent.md)* | Pointer to the interrupted gesture event.|

### OH_ArkUI_GestureInterruptInfo_GetSystemRecognizerType()

```c
int32_t OH_ArkUI_GestureInterruptInfo_GetSystemRecognizerType(const ArkUI_GestureInterruptInfo* event)
```

**Description**

Obtains the type of the system built-in gesture to trigger.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_GestureInterruptInfo](capi-arkui-nativemodule-arkui-gestureinterruptinfo.md)* event | Pointer to the gesture interruption callback event.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Type of the system built-in gesture to trigger. The value is defined in [ArkUI_GestureRecognizerType](#arkui_gesturerecognizertype). If the triggered gesture is not a built-in gesture, **-1** is returned.|

### OH_ArkUI_GestureInterruptInfo_GetTouchRecognizers()

```c
int32_t OH_ArkUI_GestureInterruptInfo_GetTouchRecognizers(const ArkUI_GestureInterruptInfo* info,ArkUI_TouchRecognizerHandleArray* recognizers, int32_t* size)
```

**Description**

Obtains touch recognizers from gesture interruption information.

**Since**: 15

**Parameters**

| Name                                                                                            | Description|
|-------------------------------------------------------------------------------------------------| -- |
| const [ArkUI_GestureInterruptInfo](capi-arkui-nativemodule-arkui-gestureinterruptinfo.md)* info | Pointer to the gesture interruption information.|
| [ArkUI_TouchRecognizerHandleArray](capi-arkui-nativemodule-arkui-touchrecognizerhandlearray.md)* recognizers  | Pointer to the touch recognizer handle array.|
| int32_t* size                                                                                   | Pointer to the size of the touch recognizer array.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TouchRecognizer_GetNodeHandle()

```c
ArkUI_NodeHandle OH_ArkUI_TouchRecognizer_GetNodeHandle(const ArkUI_TouchRecognizerHandle recognizer)
```

**Description**

Obtains the component handle corresponding to a touch recognizer.

**Since**: 15

**Parameters**

| Name                                             | Description|
|--------------------------------------------------| -- |
| const [ArkUI_TouchRecognizerHandle](capi-arkui-nativemodule-arkui-touchrecognizerhandle.md) recognizer | Handle to the touch recognizer.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) | Component handle corresponding to the touch recognizer.|

### OH_ArkUI_TouchRecognizer_CancelTouch()

```c
int32_t OH_ArkUI_TouchRecognizer_CancelTouch(ArkUI_TouchRecognizerHandle recognizer, ArkUI_GestureInterruptInfo* info)
```

**Description**

Sends a cancel touch event to a touch recognizer in a gesture interruption callback. This API is suitable for scenarios such as nested scrolling, where the parent component needs to take over scroll control. This API can be used to cancel the touch event of the child component touch recognizer to avoid gesture conflicts.

**Since**: 15

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TouchRecognizerHandle](capi-arkui-nativemodule-arkui-touchrecognizerhandle.md) recognizer | Handle to the touch recognizer.|
| [ArkUI_GestureInterruptInfo](capi-arkui-nativemodule-arkui-gestureinterruptinfo.md)* info | Pointer to the gesture interruption information.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_GestureEvent_GetActionType()

```c
ArkUI_GestureEventActionType OH_ArkUI_GestureEvent_GetActionType(const ArkUI_GestureEvent* event)
```

**Description**

Obtains the gesture event type.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_GestureEvent](capi-arkui-nativemodule-arkui-gestureevent.md)* event | Pointer to the gesture event.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_GestureEventActionType](#arkui_gestureeventactiontype) | Gesture event action type. |

### OH_ArkUI_GestureEvent_GetRawInputEvent()

```c
const ArkUI_UIInputEvent* OH_ArkUI_GestureEvent_GetRawInputEvent(const ArkUI_GestureEvent* event)
```

**Description**

Obtains the original input event of the gesture.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_GestureEvent](capi-arkui-nativemodule-arkui-gestureevent.md)* event | Pointer to the gesture event.|

**Returns**

| Type                           | Description|
|-------------------------------| -- |
| const [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* | Pointer to the input event of the gesture event.|

### OH_ArkUI_LongPress_GetRepeatCount()

```c
int32_t OH_ArkUI_LongPress_GetRepeatCount(const ArkUI_GestureEvent* event)
```

**Description**

Checks whether the event is a repeated trigger event.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_GestureEvent](capi-arkui-nativemodule-arkui-gestureevent.md)* event | Pointer to the gesture event.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Whether the event is a repeated trigger event. The value **1** means that the event is a repeated trigger event, and **0** means the opposite.|

### OH_ArkUI_PanGesture_GetVelocity()

```c
float OH_ArkUI_PanGesture_GetVelocity(const ArkUI_GestureEvent* event)
```

**Description**

Obtains the velocity of a pan gesture along the main axis.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_GestureEvent](capi-arkui-nativemodule-arkui-gestureevent.md)* event | Pointer to the gesture event.|

**Returns**

| Type| Description|
| -- | -- |
| float | Velocity of the current gesture along the main axis, which is the arithmetic square root of the sum of the squares of the velocity on the x-axis and y-axis, in px/s. |

### OH_ArkUI_PanGesture_GetVelocityX()

```c
float OH_ArkUI_PanGesture_GetVelocityX(const ArkUI_GestureEvent* event)
```

**Description**

Obtains the velocity of a pan gesture along the x-axis.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_GestureEvent](capi-arkui-nativemodule-arkui-gestureevent.md)* event | Pointer to the gesture event.|

**Returns**

| Type| Description|
| -- | -- |
| float | Velocity of the current gesture along the x-axis, in px/s. |

### OH_ArkUI_PanGesture_GetVelocityY()

```c
float OH_ArkUI_PanGesture_GetVelocityY(const ArkUI_GestureEvent* event)
```

**Description**

Obtains the velocity of a pan gesture along the y-axis.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_GestureEvent](capi-arkui-nativemodule-arkui-gestureevent.md)* event | Pointer to the gesture event.|

**Returns**

| Type| Description|
| -- | -- |
| float | Velocity of the current gesture along the y-axis, in px/s. |

### OH_ArkUI_PanGesture_GetOffsetX()

```c
float OH_ArkUI_PanGesture_GetOffsetX(const ArkUI_GestureEvent* event)
```

**Description**

Obtains the relative offset of a pan gesture along the x-axis.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_GestureEvent](capi-arkui-nativemodule-arkui-gestureevent.md)* event | Pointer to the gesture event.|

**Returns**

| Type| Description|
| -- | -- |
| float | Relative offset of the gesture along the x-axis, in px.|

### OH_ArkUI_PanGesture_GetOffsetY()

```c
float OH_ArkUI_PanGesture_GetOffsetY(const ArkUI_GestureEvent* event)
```

**Description**

Obtains the relative offset of a pan gesture along the y-axis.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_GestureEvent](capi-arkui-nativemodule-arkui-gestureevent.md)* event | Pointer to the gesture event.|

**Returns**

| Type| Description|
| -- | -- |
| float | Relative offset of the gesture along the y-axis, in px.|

### OH_ArkUI_SwipeGesture_GetAngle()

```c
float OH_ArkUI_SwipeGesture_GetAngle(const ArkUI_GestureEvent* event)
```

**Description**

Obtains the angle information of the swipe gesture, that is, the angle between the instantaneous direction of the finger swipe and the positive horizontal direction. Based on the positive horizontal direction, if the swipe direction is on the clockwise side of the positive horizontal direction, the angle ranges from 0 to 180 degrees; if the swipe direction is on the counterclockwise side of the positive horizontal direction, the angle ranges from 0 to –180 degrees.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_GestureEvent](capi-arkui-nativemodule-arkui-gestureevent.md)* event | Pointer to the gesture event.|

**Returns**

| Type| Description|
| -- | -- |
| float | Angle of the swipe gesture, that is, the angle between the instantaneous direction of finger swipe and the positive horizontal direction, in deg. |

### OH_ArkUI_SwipeGesture_GetVelocity()

```c
float OH_ArkUI_SwipeGesture_GetVelocity(const ArkUI_GestureEvent* event)
```

**Description**

Obtains the average velocity of all fingers used in the swipe gesture.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_GestureEvent](capi-arkui-nativemodule-arkui-gestureevent.md)* event | Pointer to the gesture event.|

**Returns**

| Type| Description|
| -- | -- |
| float | Average velocity of all fingers used in the swipe gesture, in px/s. |

### OH_ArkUI_RotationGesture_GetAngle()

```c
float OH_ArkUI_RotationGesture_GetAngle(const ArkUI_GestureEvent* event)
```

**Description**

Obtains the angle information of a rotation gesture.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_GestureEvent](capi-arkui-nativemodule-arkui-gestureevent.md)* event | Pointer to the gesture event.|

**Returns**

| Type| Description|
| -- | -- |
| float | Rotation angle. The unit is deg.|

### OH_ArkUI_PinchGesture_GetScale()

```c
float OH_ArkUI_PinchGesture_GetScale(const ArkUI_GestureEvent* event)
```

**Description**

Obtains the scale ratio of a pinch gesture.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_GestureEvent](capi-arkui-nativemodule-arkui-gestureevent.md)* event | Pointer to the gesture event.|

**Returns**

| Type| Description|
| -- | -- |
| float | Scale factor of the pinch gesture. A value greater than 1 indicates zooming in, and a value less than 1 indicates zooming out. |

### OH_ArkUI_PinchGesture_GetCenterX()

```c
float OH_ArkUI_PinchGesture_GetCenterX(const ArkUI_GestureEvent* event)
```

**Description**

Obtains the x-coordinate of the center of the pinch gesture, relative to the upper left corner of the current component.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_GestureEvent](capi-arkui-nativemodule-arkui-gestureevent.md)* event | Pointer to the gesture event.|

**Returns**

| Type| Description|
| -- | -- |
| float | X-coordinate of the center of the pinch gesture, in px, relative to the upper left corner of the current component.|

### OH_ArkUI_PinchGesture_GetCenterY()

```c
float OH_ArkUI_PinchGesture_GetCenterY(const ArkUI_GestureEvent* event)
```

**Description**

Obtains the y-coordinate of the center of the pinch gesture, relative to the upper left corner of the current component.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_GestureEvent](capi-arkui-nativemodule-arkui-gestureevent.md)* event | Pointer to the gesture event.|

**Returns**

| Type| Description|
| -- | -- |
| float | Y-coordinate of the center of the pinch gesture, in px, relative to the upper left corner of the current component.|

### OH_ArkUI_GestureEvent_GetNode()

```c
ArkUI_NodeHandle OH_ArkUI_GestureEvent_GetNode(const ArkUI_GestureEvent* event)
```

**Description**

Obtains the ArkUI component to which the gesture is bound.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_GestureEvent](capi-arkui-nativemodule-arkui-gestureevent.md)* event | Pointer to the gesture event.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) | ArkUI component to which the gesture is bound. Returns **NULL** if the event is invalid.|

### OH_ArkUI_GetResponseRecognizersFromInterruptInfo()

```c
int32_t OH_ArkUI_GetResponseRecognizersFromInterruptInfo(const ArkUI_GestureInterruptInfo* event,ArkUI_GestureRecognizerHandleArray* responseChain, int32_t* count)
```

**Description**

Obtains information about a gesture response chain.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_GestureInterruptInfo](capi-arkui-nativemodule-arkui-gestureinterruptinfo.md)* event | Pointer to the gesture interruption callback event.|
| [ArkUI_GestureRecognizerHandleArray](capi-arkui-nativemodule-arkui-gesturerecognizerhandlearray.md)* responseChain | Pointer to an array of gesture recognizer handles on the response chain.|
| int32_t* count | Pointer to the number of gesture recognizer handles on the response chain.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_SetGestureRecognizerEnabled()

```c
int32_t OH_ArkUI_SetGestureRecognizerEnabled(ArkUI_GestureRecognizer* recognizer, bool enabled)
```

**Description**

Sets the enabled state of a gesture recognizer.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance.|
| bool enabled | Whether to enable the gesture recognizer. The value **true** means to enable, and **false** means the opposite. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_SetGestureRecognizerLimitFingerCount()

```c
int32_t OH_ArkUI_SetGestureRecognizerLimitFingerCount(ArkUI_GestureRecognizer* recognizer, bool limitFingerCount)
```

**Description**

Sets whether to enable strict finger count checking. If this feature is enabled and the actual number of touch fingers does not match the set number, the gesture recognition fails.

**Since**: 15

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance.|
| bool limitFingerCount | Whether to enable strict finger count checking. <br>**true**: Enforce the exact number of fingers touching the screen.<br>**false**: Do not enforce the exact number of fingers touching the screen.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_GetGestureRecognizerEnabled()

```c
bool OH_ArkUI_GetGestureRecognizerEnabled(ArkUI_GestureRecognizer* recognizer)
```

**Description**

Obtains the enabled state of a gesture recognizer.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance.|

**Returns**

| Type| Description|
| -- | -- |
| bool | **true**: enabled.<br>         **false**: disabled.|

### OH_ArkUI_GetGestureRecognizerState()

```c
int32_t OH_ArkUI_GetGestureRecognizerState(ArkUI_GestureRecognizer* recognizer, ArkUI_GestureRecognizerState* state)
```

**Description**

Obtains the state of a gesture recognizer.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance.|
| [ArkUI_GestureRecognizerState](#arkui_gesturerecognizerstate)* state | Pointer to the state of the gesture recognizer. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_GetGestureEventTargetInfo()

```c
int32_t OH_ArkUI_GetGestureEventTargetInfo(ArkUI_GestureRecognizer* recognizer, ArkUI_GestureEventTargetInfo** info)
```

**Description**

Obtains the information about a gesture event target.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance.|
| [ArkUI_GestureEventTargetInfo](capi-arkui-nativemodule-arkui-gestureeventtargetinfo.md)** info | Double pointer to the information about a gesture event target.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_GestureEventTargetInfo_IsScrollBegin()

```c
int32_t OH_ArkUI_GestureEventTargetInfo_IsScrollBegin(ArkUI_GestureEventTargetInfo* info, bool* ret)
```

**Description**

Obtains whether this scrollable container component is scrolled to the top.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_GestureEventTargetInfo](capi-arkui-nativemodule-arkui-gestureeventtargetinfo.md)* info | Pointer to the information about a gesture event target.|
| bool* ret | Pointer to the **ret** parameter indicating whether this scrollable container component is scrolled to the top. The value **true** means that the component is scrolled to the top, and **false** means the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_NON_SCROLLABLE_CONTAINER](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the component is not a scrollable container.|

### OH_ArkUI_GestureEventTargetInfo_IsScrollEnd()

```c
int32_t OH_ArkUI_GestureEventTargetInfo_IsScrollEnd(ArkUI_GestureEventTargetInfo* info, bool* ret)
```

**Description**

Obtains whether this scrollable container component is scrolled to the bottom.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_GestureEventTargetInfo](capi-arkui-nativemodule-arkui-gestureeventtargetinfo.md)* info | Pointer to the information about a gesture event target.|
| bool* ret | Pointer to the **ret** parameter indicating whether this scrollable container component is scrolled to the bottom. The value **true** means that the component is scrolled to the bottom, and **false** means the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_NON_SCROLLABLE_CONTAINER](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the component is not a scrollable container.|

### OH_ArkUI_GetPanGestureDirectionMask()

```c
int32_t OH_ArkUI_GetPanGestureDirectionMask(ArkUI_GestureRecognizer* recognizer,ArkUI_GestureDirectionMask* directionMask)
```

**Description**

Obtains the direction of a pan gesture. It is recommended to use **OH_ArkUI_GetGestureParam_DirectMask** (API version 18) first, which is a unified parameter query API. **OH_ArkUI_GetPanGestureDirectionMask** is an earlier API (API version 12) with the same functionality as **OH_ArkUI_GetGestureParam_DirectMask**.

**Since**: 12

**Parameters**

| Name                                                                                      | Description|
|-------------------------------------------------------------------------------------------| -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance.|
| [ArkUI_GestureDirectionMask](#variables)* directionMask                                          | Pointer to the pan direction.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_IsBuiltInGesture()

```c
bool OH_ArkUI_IsBuiltInGesture(ArkUI_GestureRecognizer* recognizer)
```

**Description**

Obtains whether a gesture is a built-in gesture.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance.|

**Returns**

| Type| Description|
| -- | -- |
| bool | **true**: built-in gesture.<br>         **false**: non-built-in gesture.|

### OH_ArkUI_GetGestureTag()

```c
int32_t OH_ArkUI_GetGestureTag(ArkUI_GestureRecognizer* recognizer, char* buffer, int32_t bufferSize, int32_t* result)
```

**Description**

Obtains the tag of a gesture recognizer.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance.|
| char* buffer | Pointer to the output buffer.|
| int32_t bufferSize | Size of the buffer, which limits the length of the gesture recognizer tag string that can be written. |
| int32_t* result | Pointer to the length of the copied string.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_BUFFER_SIZE_NOT_ENOUGH](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the storage space is insufficient.|

### OH_ArkUI_GetGestureBindNodeId()

```c
int32_t OH_ArkUI_GetGestureBindNodeId(ArkUI_GestureRecognizer* recognizer, char* nodeId, int32_t size,int32_t* result)
```

**Description**

Obtains the ID of the component bound to a gesture recognizer (in string format, that is, the value of the **nodeId** attribute you set on the ArkUI component). To obtain the system-assigned integer unique identifier, use **OH_ArkUI_GetGestureBindNodeUniqueId**.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance.|
| char* nodeId | Pointer to the component ID.|
| int32_t size | Size of the **nodeId** buffer, which limits the length of the component ID string that can be written. |
| int32_t* result | Pointer to the length of the copied string.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_BUFFER_SIZE_NOT_ENOUGH](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the storage space is insufficient.|

### OH_ArkUI_IsGestureRecognizerValid()

```c
bool OH_ArkUI_IsGestureRecognizerValid(ArkUI_GestureRecognizer* recognizer)
```

**Description**

Obtains whether a gesture recognizer is valid.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance.|

**Returns**

| Type| Description|
| -- | -- |
| bool | **true**: The gesture recognizer is valid.<br>         **false**: The gesture recognizer is invalid.|

### OH_ArkUI_ParallelInnerGestureEvent_GetUserData()

```c
void* OH_ArkUI_ParallelInnerGestureEvent_GetUserData(ArkUI_ParallelInnerGestureEvent* event)
```

**Description**

Obtains custom data in the parallel built-in gesture event.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ParallelInnerGestureEvent](capi-arkui-nativemodule-arkui-parallelinnergestureevent.md)* event | Pointer to the parallel built-in gesture event.|

**Returns**

| Type| Description|
| -- | -- |
| void* | Pointer to user-defined data.|

### OH_ArkUI_ParallelInnerGestureEvent_GetCurrentRecognizer()

```c
ArkUI_GestureRecognizer* OH_ArkUI_ParallelInnerGestureEvent_GetCurrentRecognizer(ArkUI_ParallelInnerGestureEvent* event)
```

**Description**

Obtains the current gesture recognizer in a parallel built-in gesture event.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ParallelInnerGestureEvent](capi-arkui-nativemodule-arkui-parallelinnergestureevent.md)* event | Pointer to the parallel built-in gesture event.|

**Returns**

| Type                          | Description|
|------------------------------| -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* | Pointer to the current gesture recognizer.|

### OH_ArkUI_ParallelInnerGestureEvent_GetConflictRecognizers()

```c
int32_t OH_ArkUI_ParallelInnerGestureEvent_GetConflictRecognizers(ArkUI_ParallelInnerGestureEvent* event,ArkUI_GestureRecognizerHandleArray* array, int32_t* size)
```

**Description**

Obtains the conflicting gesture recognizers in a parallel built-in gesture event.

**Since**: 12

**Parameters**

| Name                                                                                                 | Description|
|------------------------------------------------------------------------------------------------------| -- |
| [ArkUI_ParallelInnerGestureEvent](capi-arkui-nativemodule-arkui-parallelinnergestureevent.md)* event | Pointer to the parallel built-in gesture event.|
| [ArkUI_GestureRecognizerHandleArray](capi-arkui-nativemodule-arkui-gesturerecognizerhandlearray.md)* array  | Pointer to the array of conflicting gesture recognizers.|
| int32_t* size                                                                                        | Pointer to the size of the array of conflicting gesture recognizers.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_SetArkUIGestureRecognizerDisposeNotify()

```c
int32_t OH_ArkUI_SetArkUIGestureRecognizerDisposeNotify(ArkUI_GestureRecognizer* recognizer,ArkUI_GestureRecognizerDisposeNotifyCallback callback, void* userData)
```

**Description**

Sets a callback function for notifying gesture recognizer destruction.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance.|
| [ArkUI_GestureRecognizerDisposeNotifyCallback](#arkui_gesturerecognizerdisposenotifycallback) callback | Callback for notifying gesture recognizer destruction. |
| void* userData | Pointer to the user-defined data, which is passed through to the caller in the gesture recognizer object destruction notification callback. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_GetGestureParam_DirectMask()

```c
int32_t OH_ArkUI_GetGestureParam_DirectMask(ArkUI_GestureRecognizer* recognizer, ArkUI_GestureDirectionMask* directMask)
```

**Description**

Obtains the swipe direction of a gesture recognizer.

**Since**: 18

**Parameters**

| Name                                                                                      | Description|
|-------------------------------------------------------------------------------------------| -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance.|
| [ArkUI_GestureDirectionMask](#variables)* directMask                                             | Pointer to the swipe direction of the gesture recognizer.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_GetGestureParam_FingerCount()

```c
int32_t OH_ArkUI_GetGestureParam_FingerCount(ArkUI_GestureRecognizer* recognizer, int* finger)
```

**Description**

Obtains the number of fingers used by a gesture recognizer.

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance.|
| int* finger | Pointer to the number of fingers used by the gesture recognizer.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_GetGestureParam_limitFingerCount()

```c
int32_t OH_ArkUI_GetGestureParam_limitFingerCount(ArkUI_GestureRecognizer* recognizer, bool* isLimited)
```

**Description**

Checks whether a gesture recognizer has a finger count limit.

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance.|
| bool* isLimited | Pointer to the parameter indicating whether the gesture recognizer has a finger count limit. **true** indicates that the gesture recognizer has a finger count limit. **false** indicates that the gesture recognizer does not have a finger count limit.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_GetGestureParam_repeat()

```c
int32_t OH_ArkUI_GetGestureParam_repeat(ArkUI_GestureRecognizer* recognizer, bool* isRepeat)
```

**Description**

Checks whether a gesture recognizer continuously triggers event callbacks.

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance.|
| bool* isRepeat | Pointer to the parameter indicating whether the gesture recognizer continuously triggers event callbacks. The value **true** means to continuously trigger event callbacks, and false means the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_RECOGNIZER_TYPE_NOT_SUPPORTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the gesture recognizer type is not supported.|

### OH_ArkUI_GetGestureParam_distance()

```c
int32_t OH_ArkUI_GetGestureParam_distance(ArkUI_GestureRecognizer* recognizer, double* distance)
```

**Description**

Obtains the allowed movement distance range for a gesture recognizer.

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance.|
| double* distance | Pointer to the allowed movement distance range of the gesture recognizer. The unit is px.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_RECOGNIZER_TYPE_NOT_SUPPORTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the gesture recognizer type is not supported.|

### OH_ArkUI_GetGestureParam_speed()

```c
int32_t OH_ArkUI_GetGestureParam_speed(ArkUI_GestureRecognizer* recognizer, double* speed)
```

**Description**

Obtains the minimum swipe speed recognized by a gesture recognizer.

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance.|
| double* speed | Pointer to the minimum swipe speed recognized by the gesture recognizer. The unit is px/s.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_RECOGNIZER_TYPE_NOT_SUPPORTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the gesture recognizer type is not supported.|

### OH_ArkUI_GetGestureParam_duration()

```c
int32_t OH_ArkUI_GetGestureParam_duration(ArkUI_GestureRecognizer* recognizer, int* duration)
```

**Description**

Obtains the minimum duration required to trigger a long press by a gesture recognizer.

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance.|
| int* duration | Pointer to the minimum duration for a long press. The unit is ms.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_RECOGNIZER_TYPE_NOT_SUPPORTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the gesture recognizer type is not supported.|

### OH_ArkUI_GetGestureParam_angle()

```c
int32_t OH_ArkUI_GetGestureParam_angle(ArkUI_GestureRecognizer* recognizer, double* angle)
```

**Description**

Obtains the minimum angle change required for a rotation gesture to be recognized by a gesture recognizer.

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance.|
| double* angle | Pointer to the minimum angle change. The unit is deg.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_RECOGNIZER_TYPE_NOT_SUPPORTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the gesture recognizer type is not supported.|

### OH_ArkUI_GetGestureParam_distanceThreshold()

```c
int32_t OH_ArkUI_GetGestureParam_distanceThreshold(ArkUI_GestureRecognizer* recognizer, double* distanceThreshold)
```

**Description**

Obtains the movement threshold distance for gesture recognition.

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance.|
| double* distanceThreshold | Pointer to the movement distance threshold of the gesture recognizer. The unit is px.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_RECOGNIZER_TYPE_NOT_SUPPORTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the gesture recognizer type is not supported.|

### OH_ArkUI_PanGesture_SetDistanceMap()

```c
ArkUI_ErrorCode OH_ArkUI_PanGesture_SetDistanceMap(ArkUI_GestureRecognizer* recognizer, int size, int* toolTypeArray, double* distanceArray)
```

**Description**

Sets the minimum sliding distance threshold mapping for gesture recognition, which is used for scenarios where the pan gesture recognition threshold needs to be configured based on different input tool types.

**Since**: 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance.|
| int size | Number of elements in the **toolTypeArray** and **distanceArray** arrays. The value must be greater than 0 and must match the actual number of elements in **toolTypeArray** and **distanceArray**. |
| int* toolTypeArray | Pointer to the array of input event tool types. The element values are specified by [UI_INPUT_EVENT_TOOL_TYPE](./capi-ui-input-event-h.md#anonymous2)_XXX. If a value outside this range is set, the setting does not take effect. |
| double* distanceArray | Pointer to the array of minimum sliding distance thresholds. The value range is (0, +∞), in px. If 0 or a negative number is passed in, the setting does not take effect. **distanceArray[i]** indicates the minimum sliding distance threshold for the tool type corresponding to **toolTypeArray[i]**. |

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_RECOGNIZER_TYPE_NOT_SUPPORTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the gesture recognizer type is not supported.|

### OH_ArkUI_PanGesture_GetDistanceByToolType()

```c
ArkUI_ErrorCode OH_ArkUI_PanGesture_GetDistanceByToolType(ArkUI_GestureRecognizer* recognizer, int toolType, double* distance)
```

**Description**

Obtains the gesture movement threshold of the gesture recognizer. This API only supports querying thresholds for device types that have been modified through **OH_ArkUI_PanGesture_SetDistanceMap**. The default sliding threshold can be obtained by querying the [UI_INPUT_EVENT_TOOL_TYPE_UNKNOWN](capi-ui-input-event-h.md#anonymous2) type. Other types that have not been set will not return the corresponding sliding thresholds.

**Since**: 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance.|
| int toolType | Tool type of the input event. The value specified by [UI_INPUT_EVENT_TOOL_TYPE](./capi-ui-input-event-h.md#anonymous2)_XXX. Only threshold querying for device types modified by **OH_ArkUI_PanGesture_SetDistanceMap** and the [UI_INPUT_EVENT_TOOL_TYPE_UNKNOWN](./capi-ui-input-event-h.md#anonymous2) type is supported. Other types that have not been set will not return corresponding thresholds. |
| double* distance | Pointer to the movement distance threshold of the gesture recognizer. The unit is px.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_RECOGNIZER_TYPE_NOT_SUPPORTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the gesture recognizer type is not supported.|

### OH_ArkUI_SetTouchTestDoneCallback()

```c
ArkUI_ErrorCode OH_ArkUI_SetTouchTestDoneCallback(ArkUI_NodeHandle node, void* userData, void (*touchTestDone)(ArkUI_GestureEvent* event, ArkUI_GestureRecognizerHandleArray recognizers, int32_t count, void* userData))
```

**Description**

Registers a callback that is executed after all gesture recognizers are collected. When the user begins touching the screen, the system performs hit testing and collects gesture recognizers based on the touch location. Subsequently, before processing any move events, the component can use this API to determine the gesture recognizers that will participate in and compete for recognition.

**Since**: 20

**Parameters**

| Name                      | Description|
|---------------------------| -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Handle to the node on which the callback is to be set.|
| void* userData            | Pointer to the user-defined data, which is passed back to the caller as the **userData** parameter in the **touchTestDone** callback. |
| void (\*touchTestDone)([ArkUI_GestureEvent](capi-arkui-nativemodule-arkui-gestureevent.md)* event, [ArkUI_GestureRecognizerHandleArray](capi-arkui-nativemodule-arkui-gesturerecognizerhandlearray.md) recognizers, int32_t count, void* userData)             | Callback for completion of gesture recognizer collection. **event** indicates the basic information about the gesture, **recognizers** indicates the gesture recognizer array, **count** indicates the number of gesture recognizers, and **userData** indicates the user-defined data.|

**Returns**

| Type                                                      | Description|
|----------------------------------------------------------| -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_GestureInterrupter_GetUserData()

```c
void* OH_ArkUI_GestureInterrupter_GetUserData(ArkUI_GestureInterruptInfo* event)
```

**Description**

Obtains the custom data from a gesture interruption event.

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_GestureInterruptInfo](capi-arkui-nativemodule-arkui-gestureinterruptinfo.md)* event | Pointer to the gesture interruption information.|

**Returns**

| Type| Description|
| -- | -- |
| void* | Pointer to user-defined data.|

### OH_ArkUI_PreventGestureRecognizerBegin()

```c
ArkUI_ErrorCode OH_ArkUI_PreventGestureRecognizerBegin(ArkUI_GestureRecognizer* recognizer)
```

**Description**

Prevents a gesture recognizer from participating in the current gesture recognition before all fingers are lifted. This is suitable for scenarios where a specified gesture recognizer needs to be dynamically excluded during the gesture competition process. If the system has already determined the result of the gesture recognizer (regardless of success or failure), calling this API will be ineffective.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_LongPressGesture_SetAllowableMovement()

```c
ArkUI_ErrorCode OH_ArkUI_LongPressGesture_SetAllowableMovement(ArkUI_GestureRecognizer* recognizer, double allowableMovement)
```

**Description**

Sets the maximum movement distance allowed for gesture recognition by the long press gesture recognizer.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance.|
| double allowableMovement | Maximum movement distance of the gesture recognized by the long-pressing gesture recognizer.<br>Unit: px.<br>Value range: (0, +∞). If the value is set to less than or equal to 0, the default value **15** is used. |

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>  Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>  Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>  Returns [ARKUI_ERROR_CODE_RECOGNIZER_TYPE_NOT_SUPPORTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the gesture recognizer type is not supported.|

### OH_ArkUI_LongPressGesture_GetAllowableMovement()

```c
ArkUI_ErrorCode OH_ArkUI_LongPressGesture_GetAllowableMovement(ArkUI_GestureRecognizer* recognizer, double* allowableMovement)
```

**Description**

Obtains the maximum movement distance allowed for gesture recognition by the long press gesture recognizer.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer instance.|
| double* allowableMovement | Pointer to the maximum movement distance of the gesture recognized by the long-press gesture recognizer, in px. |

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>  Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>Returns [ARKUI_ERROR_CODE_RECOGNIZER_TYPE_NOT_SUPPORTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the gesture recognizer type is not supported.|

### OH_ArkUI_GestureCollectInterceptInfo_GetResponseRecognizers()

```c
ArkUI_ErrorCode OH_ArkUI_GestureCollectInterceptInfo_GetResponseRecognizers(const ArkUI_GestureCollectInterceptInfo* info, ArkUI_GestureRecognizerHandleArray* array, int32_t* size)
```

**Description**

Obtains gesture recognizer handles from gesture collection interception information.

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_GestureCollectInterceptInfo](capi-arkui-nativemodule-arkui-gesturecollectinterceptinfo.md)* info | Pointer to the gesture collection interception information.|
| [ArkUI_GestureRecognizerHandleArray](capi-arkui-nativemodule-arkui-gesturerecognizerhandlearray.md)* array | Pointer to the gesture recognizer handle array.|
| int32_t* size | Pointer to the size of the gesture recognizer handle array.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_GestureCollectInterceptInfo_GetTouchRecognizers()

```c
ArkUI_ErrorCode OH_ArkUI_GestureCollectInterceptInfo_GetTouchRecognizers(const ArkUI_GestureCollectInterceptInfo* info, ArkUI_TouchRecognizerHandleArray* recognizers, int32_t* size)
```

**Description**

Obtains touch recognizer handles from gesture collection interception information.

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_GestureCollectInterceptInfo](capi-arkui-nativemodule-arkui-gesturecollectinterceptinfo.md)* info | Pointer to the gesture collection interception information.|
| [ArkUI_TouchRecognizerHandleArray](capi-arkui-nativemodule-arkui-touchrecognizerhandlearray.md)* recognizers | Pointer to the touch recognizer handle array.|
| int32_t* size | Pointer to the size of the touch recognizer handle array.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_GestureCollectInterceptInfo_SetGestureCollectIntervention()

```c
ArkUI_ErrorCode OH_ArkUI_GestureCollectInterceptInfo_SetGestureCollectIntervention(ArkUI_GestureCollectInterceptInfo* info, OH_ArkUI_GestureCollectIntervention intervention)
```

**Description**

Sets the intervention mode for gesture collection.

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_GestureCollectInterceptInfo](capi-arkui-nativemodule-arkui-gesturecollectinterceptinfo.md)* info | Pointer to the gesture collection interception information.|
| [OH_ArkUI_GestureCollectIntervention](#oh_arkui_gesturecollectintervention) intervention | Gesture collection intervention mode, which is of the [OH_ArkUI_GestureCollectIntervention](#oh_arkui_gesturecollectintervention) type.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_GetGestureBindNodeUniqueId()

```c
ArkUI_ErrorCode OH_ArkUI_GetGestureBindNodeUniqueId(const ArkUI_GestureRecognizer* recognizer, int32_t* uniqueId)
```

**Description**

Obtains the unique ID of the component bound to a gesture recognizer.

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer.|
| int32_t* uniqueId | Pointer to the unique ID of the component bound to the gesture recognizer.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TouchRecognizer_IsHostBelongsTo()

```c
bool OH_ArkUI_TouchRecognizer_IsHostBelongsTo(const ArkUI_TouchRecognizerHandle recognizer, int32_t uniqueId)
```

**Description**

Checks whether the node bound to the touch recognizer is a descendant node of the passed component.

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_TouchRecognizerHandle](capi-arkui-nativemodule-arkui-touchrecognizerhandle.md) recognizer | Touch recognizer handle.|
| int32_t uniqueId | Unique ID of the component, which can be obtained by [OH_ArkUI_GetGestureBindNodeUniqueId](#oh_arkui_getgesturebindnodeuniqueid). |

**Returns**

| Type| Description|
| -- | -- |
| bool | **true** if the node bound to the touch recognizer is a descendant node of the passed component; **false** otherwise.|

### OH_ArkUI_GestureRecognizer_IsHostBelongsTo()

```c
bool OH_ArkUI_GestureRecognizer_IsHostBelongsTo(const ArkUI_GestureRecognizer* recognizer, int32_t uniqueId)
```

**Description**

Checks whether the node bound to the gesture recognizer is a descendant node of the passed component.

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_GestureRecognizer](capi-arkui-nativemodule-arkui-gesturerecognizer.md)* recognizer | Pointer to the gesture recognizer.|
| int32_t uniqueId | Unique ID of the component, which can be obtained by [OH_ArkUI_GetGestureBindNodeUniqueId](#oh_arkui_getgesturebindnodeuniqueid). |

**Returns**

| Type| Description|
| -- | -- |
| bool | **true** if the node bound to the gesture recognizer is a descendant node of the passed component; **false** otherwise.|