# ui_input_event.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=68136ebb64bac07de49f9c3b374e4134caccec1e translatedAt=2026-08-29T09:58:37.243Z pushedAt=2026-08-31T01:20:49.990Z -->

## Overview

Provides input event definitions for ArkUI on the native side, including touch, mouse, axis, and key events. It also supports event attribute obtaining, event bubbling control, and event cloning, enabling native components to identify and process user input.

**File to include**: <arkui/ui_input_event.h>

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_EventModule](capi-arkui-eventmodule.md)

**Sample**: <!--RP1-->[NdkInputEvent](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NdkInputEvent)<!--RP1End-->, <!--RP2-->[CoastingAxisEventNDK](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/CoastingAxisEventNDK)<!--RP2End-->

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md) | ArkUI_UIInputEvent | Defines **ArkUI_UIInputEvent**, which represents the UI input event in ArkUI. It is used by the event APIs in the **ArkUI_EventModule** module to transfer and process input event information. It is applicable to scenarios where user input events need to be identified, distributed, or responded to. |
| [ArkUI_CoastingAxisEvent](capi-arkui-nativemodule-arkui-coastingaxisevent.md) | ArkUI_CoastingAxisEvent | Defines the coasting axis event. When the user performs a two-finger swipe on the touchpad, the system constructs a swipe event based on the finger lift speed, following a preset attenuation curve. You can listen for this event to handle the coasting effect immediately after processing regular axis events. This event is only dispatched if two conditions are met: 1. The user executes a two-finger swipe on the touchpad. 2. A component registered for the [NODE_ON_COASTING_AXIS_EVENT](capi-native-node-h.md#arkui_nodeeventtype) event (via [registerNodeEvent](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent)) exists at the pointer's position. When the event is no longer needed, call [unregisterNodeEvent](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#unregisternodeevent) to unregister the event listener to prevent the callback from being triggered repeatedly. |
| [ArkUI_TouchTestInfo](capi-arkui-nativemodule-arkui-touchtestinfo.md) | ArkUI_TouchTestInfo | Defines touch test information, which is used to obtain the touch test policy, IDs of child components involved in the hit test, and touch test information item list during the hit test. This is applicable to scenarios where you need to obtain detailed hit test information from the touch event of a child component to customize the hit test logic and optimize the distribution and response of touch events. This event is dispatched only if the user registers the [NODE_ON_CHILD_TOUCH_TEST](capi-native-node-h.md#arkui_nodeeventtype) event using [registerNodeEvent](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent). The touch test information includes the touch test policy, IDs of child components that need to participate in the hit test, and a list of touch test information items. |
| [ArkUI_TouchTestInfoItem](capi-arkui-nativemodule-arkui-touchtestinfoitem.md) | ArkUI_TouchTestInfoItem | Defines touch test information items. Touch test information items contain information about child components in a touch test. They are applicable to scenarios where child component information needs to be obtained and identified during a touch test. You can use APIs such as [OH_ArkUI_TouchTestInfoItem_GetX](#oh_arkui_touchtestinfoitem_getx) and [OH_ArkUI_TouchTestInfoItem_GetY](#oh_arkui_touchtestinfoitem_gety) to obtain child component information, helping you process touch test results. |
| [ArkUI_TouchTestInfoItem*](capi-arkui-nativemodule-arkui-touchtestinfoitemhandle.md) | ArkUI_TouchTestInfoItemHandle | Defines the handle of a touch test information item, which is used to indicate the touch test information item in the touch test process. For details about the touch test APIs, see [ui_input_event.h](capi-ui-input-event-h.md). |
| [ArkUI_TouchTestInfoItemHandle*](capi-arkui-nativemodule-arkui-touchtestinfoitemhandlearray.md) | ArkUI_TouchTestInfoItemArray | Defines the handle array of touch test information items, which is used to indicate multiple touch test information items. During the distribution and test of touch events, this array type can be used to manage and access multiple touch test results in a unified manner. It is applicable to scenarios where multiple touch test information items need to be processed at the same time. |

### Enums

| Name                                                 | typedef Keyword| Description|
|-----------------------------------------------------| -- | -- |
| [ArkUI_UIInputEvent_Type](#arkui_uiinputevent_type) | ArkUI_UIInputEvent_Type | Enumerates the UI input event types.|
| [anonymous1](#anonymous1)                       | - | Enumerates the action types of the input event.|
| [anonymous2](#anonymous2)                       | - | Enumerates the tool types of the input event.|
| [anonymous3](#anonymous3)                       | - | Enumerates the source types of the input event.|
| [HitTestMode](#hittestmode)                         | HitTestMode | Enumerates the hit test modes.|
| [anonymous4](#anonymous4)                       | - | Enumerates the action types of the mouse event.|
| [anonymous5](#anonymous5)                       | - | Enumerates the button types of the mouse event.|
| [ArkUI_ModifierKeyName](#arkui_modifierkeyname)     | ArkUI_ModifierKeyName | Enumerates the modifier keys. |
| [anonymous6](#anonymous6)                       | - | Enumerates the axis types for focus axis events.|
| [ArkUI_InteractionHand](#arkui_interactionhand)     | ArkUI_InteractionHand | Defines whether the touch event is from the left or right hand.|
| [anonymous7](#anonymous7)                       | - | Enumerates the action types for axis events.|
| [anonymous8](#anonymous8)                       | - | Enumerates the axis types for axis events.|
| [ArkUI_CoastingAxisEventPhase](#arkui_coastingaxiseventphase) | ArkUI_CoastingAxisEventPhase | Enumerates the phases of coasting axis events.|
| [ArkUI_CompetitionStrategy](#arkui_competitionstrategy) | ArkUI_CompetitionStrategy | Strategy that determines whether the gesture identification result between the event injector and the injected end is in a competition scenario. This strategy determines how the event injector interacts with the gesture processing logic of the injected end. In non-competition scenarios, the gestures of the two parties are triggered simultaneously. In competition scenarios, only the gesture of one party is triggered.|
| [ArkUI_TouchTestStrategy](#arkui_touchteststrategy) | ArkUI_TouchTestStrategy | Defines the touch test policy.|
| [ArkUI_CrownEvent_Action](#arkui_crownevent_action) | ArkUI_CrownEvent_Action | Defines the phases of a crown event. |

### Functions

| Name| Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| -- |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [int32_t OH_ArkUI_UIInputEvent_GetType(const ArkUI_UIInputEvent* event)](#oh_arkui_uiinputevent_gettype) | Obtains the type of a UI input event. Before accessing an **ArkUI_UIInputEvent** pointer object, you are advised to use this API to determine the type of the input event. This API returns one of the values defined in [ArkUI_UIInputEvent_Type](#arkui_uiinputevent_type). It helps ensure compatibility with subsequent accessors. For example, if the event is a touch event, which is directional, you can use OH_ArkUI_UIInputEvent_GetXXX or OH_ArkUI_PointerEvent_GetXXX for access. Using OH_ArkUI_KeyEvent_GetXXX to access the event may produce undefined behavior. For unsupported event types, this API returns the default value **0**.                                                                                                                                                                                                                                                       |
| [int32_t OH_ArkUI_UIInputEvent_GetAction(const ArkUI_UIInputEvent* event)](#oh_arkui_uiinputevent_getaction) | Obtains the action type of an input event. The action type defines the phase of a basic event (for example, start or end) and characterizes its behavior, such as touch down or touch up. Action types are specific to the event category: UI_TOUCH_EVENT_ACTION_XXX for touch events and UI_MOUSE_EVENT_ACTION_XXX for mouse events.                                                                                                                                                                                                                                                                                                                                                                                                                  |
| [int32_t OH_ArkUI_UIInputEvent_GetSourceType(const ArkUI_UIInputEvent* event)](#oh_arkui_uiinputevent_getsourcetype) | Obtains the source type of a UI input event. The source represents the physical device, such as a touchscreen or mouse device, that generates the input event. It is defined by [UI_INPUT_EVENT_SOURCE_TYPE](#anonymous3). This is different from the input tool, which is the device used to interact with the source, for example, a finger or stylus. However, in certain cases, the input source and the input tool can be the same. For example, a mouse device acts as both the source and tool for click events. For key events, obtaining the source type is not supported, and in such cases, the API will return an **unknown** value. |
| [int32_t OH_ArkUI_UIInputEvent_GetToolType(const ArkUI_UIInputEvent* event)](#oh_arkui_uiinputevent_gettooltype) | Obtains the tool type of a UI input event. The input tool is a tool that operates an input source device to generate an event, such as a finger or a stylus pen. The input tool does not directly generate events but can drive the input source device to continuously generate events. The returned type is defined by the enumerated value of **UI_INPUT_EVENT_TOOL_TYPE_XXX**.                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| [int64_t OH_ArkUI_UIInputEvent_GetEventTime(const ArkUI_UIInputEvent* event)](#oh_arkui_uiinputevent_geteventtime) | Obtains the time when a specified UI input event occurs. The unit is ns.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| [uint32_t OH_ArkUI_PointerEvent_GetPointerCount(const ArkUI_UIInputEvent* event)](#oh_arkui_pointerevent_getpointercount) | Obtains the number of contact points from a pointer event (such as a touch, mouse, or axis event). Pointer events are typically events that carry position information, such as touch events, where the location of the event can be determined. Non-pointer events, such as key events, do not have position information and do not involve touch points. This API always returns **0** for key events. For touch events, this API returns the number of active touch points, for example, fingers on the screen. For mouse and axis events, this API always returns **1**, as they are single-pointer interactions. |
| [int32_t OH_ArkUI_PointerEvent_GetPointerId(const ArkUI_UIInputEvent* event, uint32_t pointerIndex)](#oh_arkui_pointerevent_getpointerid) | Obtains the unique ID of a contact point from a pointer event (such as a touch, mouse, or axis event). The ID distinguishes between multiple touch points from the same input device. The return value itself does not have any other meaning beyond identifying the touch point.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| [int32_t OH_ArkUI_PointerEvent_GetChangedPointerId(const ArkUI_UIInputEvent* event, uint32_t* pointerIndex)](#oh_arkui_pointerevent_getchangedpointerid) | Obtains the finger ID that triggers the current event. |
| [float OH_ArkUI_PointerEvent_GetCurrentLocalX(const ArkUI_UIInputEvent* event)](#oh_arkui_pointerevent_getcurrentlocalx) | Obtains the X coordinate relative to the upper left corner of the current component from a [pointer event](../../ui/arkts-interaction-capability-overview.md#pointer-event)(such as a touch event, mouse event, or axis event) based on the real-time location.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| [float OH_ArkUI_PointerEvent_GetCurrentLocalXByIndex(const ArkUI_UIInputEvent* event, uint32_t pointerIndex)](#oh_arkui_pointerevent_getcurrentlocalxbyindex) | Obtains the X coordinate of a specific contact point relative to the upper left corner of the current component from a [pointer event](../../ui/arkts-interaction-capability-overview.md#pointer-event)(such as a touch event, mouse event, or axis event) based on the real-time location. For all types of events, the value of **pointerIndex** is of the uint32_t type and cannot be less than 0. For mouse and axis events, the value of **pointerIndex** must be 0. For touch events, the value of **pointerIndex** must be less than the number of touch points in the current event. This API obtains the X-coordinate of a specific touch point relative to the upper left corner of the current component based on the given index.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| [float OH_ArkUI_PointerEvent_GetCurrentLocalY(const ArkUI_UIInputEvent* event)](#oh_arkui_pointerevent_getcurrentlocaly) | Obtains the Y coordinate relative to the upper left corner of the current component from a [pointer event](../../ui/arkts-interaction-capability-overview.md#pointer-event)(such as a touch event, mouse event, or axis event) based on the real-time location.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| [float OH_ArkUI_PointerEvent_GetCurrentLocalYByIndex(const ArkUI_UIInputEvent* event, uint32_t pointerIndex)](#oh_arkui_pointerevent_getcurrentlocalybyindex) | Obtains the Y coordinate of a specific contact point relative to the upper left corner of the current component from a [pointer event](../../ui/arkts-interaction-capability-overview.md#pointer-event)(such as a touch event, mouse event, or axis event) based on the real-time location. For all types of events, an index value less than 0 is considered invalid. For mouse and axis events, an index value other than 0 is considered invalid. For touch events, this API is used to obtain the Y coordinate of a specific contact point relative to the upper left corner of the current component based on the given index.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| [float OH_ArkUI_PointerEvent_GetX(const ArkUI_UIInputEvent* event)](#oh_arkui_pointerevent_getx) | Obtains the x-coordinate relative to the upper left corner of the current component from a pointer event (such as a touch, mouse, or axis event).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| [float OH_ArkUI_PointerEvent_GetXByIndex(const ArkUI_UIInputEvent* event, uint32_t pointerIndex)](#oh_arkui_pointerevent_getxbyindex) | Obtains the x-coordinate of a specific contact point relative to the upper left corner of the current component from a pointer event (such as a touch, mouse, or axis event). For mouse and axis events, this API returns the default value of **0.0f** if the given index is greater than 0.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| [float OH_ArkUI_PointerEvent_GetY(const ArkUI_UIInputEvent* event)](#oh_arkui_pointerevent_gety) | Obtains the y-coordinate relative to the upper left corner of the current component from a pointer event (such as a touch, mouse, or axis event).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| [float OH_ArkUI_PointerEvent_GetYByIndex(const ArkUI_UIInputEvent* event, uint32_t pointerIndex)](#oh_arkui_pointerevent_getybyindex) | Obtains the y-coordinate of a specific contact point relative to the upper left corner of the current component from a pointer event (such as a touch, mouse, or axis event). For mouse and axis events, this API returns the default value of **0.0f** if the given index is greater than 0.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| [float OH_ArkUI_PointerEvent_GetWindowX(const ArkUI_UIInputEvent* event)](#oh_arkui_pointerevent_getwindowx) | Obtains the x-coordinate relative to the upper left corner of the current application window from a pointer event (such as a touch, mouse, or axis event).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| [float OH_ArkUI_PointerEvent_GetWindowXByIndex(const ArkUI_UIInputEvent* event, uint32_t pointerIndex)](#oh_arkui_pointerevent_getwindowxbyindex) | Obtains the x-coordinate of a specific contact point relative to the upper left corner of the current application window from a pointer event (such as a touch, mouse, or axis event). For mouse and axis events, this API returns the default value of **0.0f** if the given index is greater than 0.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| [float OH_ArkUI_PointerEvent_GetWindowY(const ArkUI_UIInputEvent* event)](#oh_arkui_pointerevent_getwindowy) | Obtains the y-coordinate relative to the upper left corner of the current application window from a pointer event (such as a touch, mouse, or axis event).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| [float OH_ArkUI_PointerEvent_GetWindowYByIndex(const ArkUI_UIInputEvent* event, uint32_t pointerIndex)](#oh_arkui_pointerevent_getwindowybyindex) | Obtains the y-coordinate of a specific contact point relative to the upper left corner of the current application window from a pointer event (such as a touch, mouse, or axis event). For mouse and axis events, this API returns the default value of **0.0f** if the given index is greater than 0.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| [float OH_ArkUI_PointerEvent_GetDisplayX(const ArkUI_UIInputEvent* event)](#oh_arkui_pointerevent_getdisplayx) | Obtains the x-coordinate relative to the upper left corner of the current screen from a pointer event (such as a touch, mouse, or axis event).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| [float OH_ArkUI_PointerEvent_GetDisplayXByIndex(const ArkUI_UIInputEvent* event, uint32_t pointerIndex)](#oh_arkui_pointerevent_getdisplayxbyindex) | Obtains the x-coordinate of a specific contact point relative to the upper left corner of the current screen from a pointer event (such as a touch, mouse, or axis event). For mouse and axis events, this API returns the default value of **0.0f** if the given index is greater than 0.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| [float OH_ArkUI_PointerEvent_GetDisplayY(const ArkUI_UIInputEvent* event)](#oh_arkui_pointerevent_getdisplayy) | Obtains the y-coordinate relative to the upper left corner of the current screen from a pointer event (such as a touch, mouse, or axis event).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| [float OH_ArkUI_PointerEvent_GetDisplayYByIndex(const ArkUI_UIInputEvent* event, uint32_t pointerIndex)](#oh_arkui_pointerevent_getdisplayybyindex) | Obtains the y-coordinate of a specific contact point relative to the upper left corner of the current screen from a pointer event (such as a touch, mouse, or axis event). For mouse and axis events, this API returns the default value of **0.0f** if the given index is greater than 0.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| [float OH_ArkUI_PointerEvent_GetGlobalDisplayX(const ArkUI_UIInputEvent* event)](#oh_arkui_pointerevent_getglobaldisplayx) | Obtains the x-coordinate relative to the global display from a pointer event (such as a touch, mouse, or axis event). The position information can be obtained only from a [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md) event.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| [float OH_ArkUI_PointerEvent_GetGlobalDisplayXByIndex(const ArkUI_UIInputEvent* event, uint32_t pointerIndex)](#oh_arkui_pointerevent_getglobaldisplayxbyindex) | Obtains the x-coordinate relative to the global display from a pointer event (such as a touch, mouse, or axis event). Position information can only be obtained from pointer events. For mouse and axis events, if the provided **pointerIndex** is greater than 0, this API always returns the default value **0.0f**. |
| [float OH_ArkUI_PointerEvent_GetGlobalDisplayY(const ArkUI_UIInputEvent* event)](#oh_arkui_pointerevent_getglobaldisplayy) | Obtains the y-coordinate relative to the global display from a pointer event (such as a touch, mouse, or axis event). The position information can be obtained only from a [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md) event.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| [float OH_ArkUI_PointerEvent_GetGlobalDisplayYByIndex(const ArkUI_UIInputEvent* event, uint32_t pointerIndex)](#oh_arkui_pointerevent_getglobaldisplayybyindex) | Obtains the y-coordinate relative to the global display from a pointer event (such as a touch, mouse, or axis event). Position information can only be obtained from pointer events. For mouse and axis events, if the provided **pointerIndex** is greater than 0, this API always returns the default value **0.0f**. |
| [float OH_ArkUI_PointerEvent_GetPressure(const ArkUI_UIInputEvent* event, uint32_t pointerIndex)](#oh_arkui_pointerevent_getpressure) | Obtains the pressure applied to the touchscreen from a pointer event (such as a touch event).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| [float OH_ArkUI_PointerEvent_GetTiltX(const ArkUI_UIInputEvent* event, uint32_t pointerIndex)](#oh_arkui_pointerevent_gettiltx) | Obtains the angle relative to the YZ plane from a pointer event (for example, a touch event). The value range is [-90, 90], in deg. A positive value indicates a rightward tilt. This API is applicable only to stylus-based touch events from devices that support tilt angle reporting.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| [float OH_ArkUI_PointerEvent_GetTiltY(const ArkUI_UIInputEvent* event, uint32_t pointerIndex)](#oh_arkui_pointerevent_gettilty) | Obtains the angle relative to the XZ plane from a pointer event (for example, a touch event). The value range is [-90, 90], in deg. A positive value indicates a downward tilt. This API is applicable only to stylus-based touch events from devices that support tilt angle reporting.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| [int32_t OH_ArkUI_PointerEvent_GetRollAngle(const ArkUI_UIInputEvent* event, double* rollAngle)](#oh_arkui_pointerevent_getrollangle) | Obtains the rotation angle of the stylus around the z-axis from a UI input event.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| [float OH_ArkUI_PointerEvent_GetTouchAreaWidth(const ArkUI_UIInputEvent* event, uint32_t pointerIndex)](#oh_arkui_pointerevent_gettouchareawidth) | Obtains the width of the touch area for a pointer event. This API is applicable only to touch events generated by finger operations.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| [float OH_ArkUI_PointerEvent_GetTouchAreaHeight(const ArkUI_UIInputEvent* event, uint32_t pointerIndex)](#oh_arkui_pointerevent_gettouchareaheight) | Obtains the height of the touch area for a pointer event. This API is applicable only to touch events generated by finger operations.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| [int32_t OH_ArkUI_PointerEvent_GetInteractionHand(const ArkUI_UIInputEvent *event, ArkUI_InteractionHand *hand)](#oh_arkui_pointerevent_getinteractionhand) | Checks whether an event is triggered by a left-hand or right-hand tap. This API is only effective on some touch devices.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| [int32_t OH_ArkUI_PointerEvent_GetInteractionHandByIndex(const ArkUI_UIInputEvent *event, int32_t pointerIndex, ArkUI_InteractionHand *hand)](#oh_arkui_pointerevent_getinteractionhandbyindex) | Checks whether an event is triggered by a left-hand or right-hand tap. This API is only effective on some touch devices.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| [uint32_t OH_ArkUI_PointerEvent_GetHistorySize(const ArkUI_UIInputEvent* event)](#oh_arkui_pointerevent_gethistorysize) | Obtains the number of historical events from a [pointer event](../../ui/arkts-interaction-capability-overview.md#pointer-event). Pointer events supported by this API contain only touch and mouse events. A historical event is the raw event that occurs between the current event and the previous event. This API is applicable only to the move phase (touch or mouse movement) of a pointer event. If this API is called in other states, the default value **0** is returned. Touch events are supported since API version 12, and mouse events are supported since API version 26.0.0.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| [int64_t OH_ArkUI_PointerEvent_GetHistoryEventTime(const ArkUI_UIInputEvent* event, uint32_t historyIndex)](#oh_arkui_pointerevent_gethistoryeventtime) | Obtains the occurrence time of a historical event from a pointer event. Pointer events supported by this API contain only touch and mouse events. Touch events are supported since API version 12, and mouse events are supported since API version 26.0.0.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| [uint32_t OH_ArkUI_PointerEvent_GetHistoryPointerCount(const ArkUI_UIInputEvent* event, uint32_t historyIndex)](#oh_arkui_pointerevent_gethistorypointercount) | Obtains the number of contact points in a specific historical event from a pointer event. Pointer events supported by this API contain only touch events.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| [int32_t OH_ArkUI_PointerEvent_GetHistoryPointerId(const ArkUI_UIInputEvent* event, uint32_t pointerIndex, uint32_t historyIndex)](#oh_arkui_pointerevent_gethistorypointerid) | Obtains the unique ID of a contact point in a specific historical event from a pointer event. Pointer events supported by this API contain only touch events. The ID distinguishes between multiple touch points from the same input device. The return value itself does not have any other meaning beyond identifying the touch point.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| [float OH_ArkUI_PointerEvent_GetHistoryX(const ArkUI_UIInputEvent* event, uint32_t pointerIndex, uint32_t historyIndex)](#oh_arkui_pointerevent_gethistoryx) | Obtains the X-coordinate of a specific contact point in a specific historical event relative to the upper left corner of the current component from a pointer event. Pointer events supported by this API contain only touch and mouse events. For mouse events, this API returns the default value **0.0f** if the given value of **pointerIndex** is greater than **0**. Touch events are supported since API version 12, and mouse events are supported since API version 26.0.0.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| [float OH_ArkUI_PointerEvent_GetHistoryY(const ArkUI_UIInputEvent* event, uint32_t pointerIndex, uint32_t historyIndex)](#oh_arkui_pointerevent_gethistoryy) | Obtains the Y-coordinate of a specific contact point in a specific historical event relative to the upper left corner of the current component from a pointer event. Pointer events supported by this API contain only touch and mouse events. For mouse events, this API returns the default value **0.0f** if the given value of **pointerIndex** is greater than **0**. Touch events are supported since API version 12, and mouse events are supported since API version 26.0.0.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| [float OH_ArkUI_PointerEvent_GetHistoryWindowX(const ArkUI_UIInputEvent* event, uint32_t pointerIndex, uint32_t historyIndex)](#oh_arkui_pointerevent_gethistorywindowx) | Obtains the X-coordinate of a specific contact point in a specific historical event relative to the upper left corner of the current application window from a pointer event. Pointer events supported by this API contain only touch and mouse events. For mouse events, this API returns the default value **0.0f** if the given value of **pointerIndex** is greater than **0**. Touch events are supported since API version 12, and mouse events are supported since API version 26.0.0.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| [float OH_ArkUI_PointerEvent_GetHistoryWindowY(const ArkUI_UIInputEvent* event, uint32_t pointerIndex, uint32_t historyIndex)](#oh_arkui_pointerevent_gethistorywindowy) | Obtains the Y-coordinate of a specific contact point in a specific historical event relative to the upper left corner of the current application window from a pointer event. Pointer events supported by this API contain only touch and mouse events. For mouse events, this API returns the default value **0.0f** if the given value of **pointerIndex** is greater than **0**. Touch events are supported since API version 12, and mouse events are supported since API version 26.0.0.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| [float OH_ArkUI_PointerEvent_GetHistoryDisplayX(const ArkUI_UIInputEvent* event, uint32_t pointerIndex, uint32_t historyIndex)](#oh_arkui_pointerevent_gethistorydisplayx) | Obtains the X-coordinate of a specific contact point in a specific historical event relative to the upper left corner of the current screen from a pointer event. Pointer events supported by this API contain only touch and mouse events. For mouse events, this API returns the default value **0.0f** if the given value of **pointerIndex** is greater than **0**. Touch events are supported since API version 12, and mouse events are supported since API version 26.0.0.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| [float OH_ArkUI_PointerEvent_GetHistoryDisplayY(const ArkUI_UIInputEvent* event, uint32_t pointerIndex, uint32_t historyIndex)](#oh_arkui_pointerevent_gethistorydisplayy) | Obtains the Y-coordinate of a specific contact point in a specific historical event relative to the upper left corner of the current screen from a pointer event. Pointer events supported by this API contain only touch and mouse events. For mouse events, this API returns the default value **0.0f** if the given value of **pointerIndex** is greater than **0**. Touch events are supported since API version 12, and mouse events are supported since API version 26.0.0.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| [float OH_ArkUI_PointerEvent_GetHistoryGlobalDisplayX(const ArkUI_UIInputEvent* event, uint32_t pointerIndex, uint32_t historyIndex)](#oh_arkui_pointerevent_gethistoryglobaldisplayx) | Obtains the X-coordinate relative to the global display for a specific touch point in a historical event from a pointer event at the given pointer index and history index. Pointer events supported by this API contain only touch and mouse events. Position information can only be obtained from pointer events. For mouse events, this API returns the default value **0.0f** if the given value of **pointerIndex** is greater than **0**. Touch events are supported since API version 20, and mouse events are supported since API version 26.0.0.                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| [float OH_ArkUI_PointerEvent_GetHistoryGlobalDisplayY(const ArkUI_UIInputEvent* event, uint32_t pointerIndex, uint32_t historyIndex)](#oh_arkui_pointerevent_gethistoryglobaldisplayy) | Obtains the Y-coordinate relative to the global display for a specific touch point in a historical event from a pointer event at the given pointer index and history index. Pointer events supported by this API contain only touch and mouse events. Position information can only be obtained from pointer events. For mouse events, this API returns the default value **0.0f** if the given value of **pointerIndex** is greater than **0**. Touch events are supported since API version 20, and mouse events are supported since API version 26.0.0.                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| [float OH_ArkUI_PointerEvent_GetHistoryPressure(const ArkUI_UIInputEvent* event, uint32_t pointerIndex, uint32_t historyIndex)](#oh_arkui_pointerevent_gethistorypressure) | Obtains the pressure applied to the touchscreen in a specific historical event from a pointer event (such as a touch event).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| [float OH_ArkUI_PointerEvent_GetHistoryTiltX(const ArkUI_UIInputEvent* event, uint32_t pointerIndex, uint32_t historyIndex)](#oh_arkui_pointerevent_gethistorytiltx) | Obtains the angle relative to the YZ plane in a specific historical event from a pointer event (such as a touch event). The value range is [-90, 90], in deg. A positive value indicates a rightward tilt.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| [float OH_ArkUI_PointerEvent_GetHistoryTiltY(const ArkUI_UIInputEvent* event, uint32_t pointerIndex, uint32_t historyIndex)](#oh_arkui_pointerevent_gethistorytilty) | Obtains the angle relative to the XZ plane in a specific historical event from a pointer event (such as a touch event). The value range is [-90, 90], in deg. A positive value indicates a downward tilt. This API is applicable only to stylus-based touch events from devices that support tilt angle reporting. |
| [float OH_ArkUI_PointerEvent_GetHistoryTouchAreaWidth(const ArkUI_UIInputEvent* event, uint32_t pointerIndex, uint32_t historyIndex)](#oh_arkui_pointerevent_gethistorytouchareawidth) | Obtains the width of the touch area in a specific historical event from a pointer event (such as a touch event).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| [float OH_ArkUI_PointerEvent_GetHistoryTouchAreaHeight(const ArkUI_UIInputEvent* event, uint32_t pointerIndex, uint32_t historyIndex)](#oh_arkui_pointerevent_gethistorytouchareaheight) | Obtains the height of the touch area in a specific historical event from a pointer event (such as a touch event).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| [double OH_ArkUI_AxisEvent_GetVerticalAxisValue(const ArkUI_UIInputEvent* event)](#oh_arkui_axisevent_getverticalaxisvalue) | Obtains the value of the vertical scroll axis for this axis event. This value is typically generated by mouse wheel scrolling or two-finger vertical swiping on a touchpad. If the value is generated by mouse wheel scrolling: 1. The reported value is in degrees, representing the angle increment of a single scroll, not the total scroll amount. 2. The reported value includes the user's scroll step configuration ([OH_ArkUI_AxisEvent_GetScrollStep](#oh_arkui_axisevent_getscrollstep)). 3. The sign of the value indicates the direction: negative for forward scrolling and positive for backward scrolling. If the value is generated by two-finger vertical swiping on a touchpad: 1. The reported value is in pixels, representing the scroll increment of a single scroll, not the total scroll amount. 2. The reported value is not affected by the user's scroll step configuration ([OH_ArkUI_AxisEvent_GetScrollStep](#oh_arkui_axisevent_getscrollstep)). 3. The sign of the value indicates the direction: When two fingers swipe from top to bottom, the reported value is negative. When two fingers swipe from bottom to top, the reported value is positive. 4. The direction is affected by the natural scrolling in the system settings. Generally, the vertical scroll axis event can only drive the response to vertical swipe gestures. However, if the scrollable directions of the swipe gestures under the mouse pointer are consistent, the vertical scroll axis event can drive these swipe gestures to respond, even if they are defined as horizontal. |
| [double OH_ArkUI_AxisEvent_GetHorizontalAxisValue(const ArkUI_UIInputEvent* event)](#oh_arkui_axisevent_gethorizontalaxisvalue) | Obtains the value of the horizontal scroll axis for this axis event. This value is generated by two-finger horizontal swiping on a touchpad. 1. The reported value is in pixels, representing the scroll increment of a single scroll, not the total scroll amount. 2. The reported value is not affected by the user's scroll step configuration ([OH_ArkUI_AxisEvent_GetScrollStep](#oh_arkui_axisevent_getscrollstep)). 3. The sign of the value indicates the direction: When two fingers swipe from left to right, the reported value is negative. When two fingers swipe from right to left, the reported value is positive. 4. The direction is affected by the natural scrolling in the system settings. |
| [double OH_ArkUI_AxisEvent_GetPinchAxisScaleValue(const ArkUI_UIInputEvent* event)](#oh_arkui_axisevent_getpinchaxisscalevalue) | Obtains the scale value of the pinch axis for this axis event. This value is generated by a two-finger pinch gesture on a touchpad. The reported scale value is relative to the initial state when the system first detects the pinch gesture, with an initial scale value of 1.0. During the pinch operation, the scale value decreases from 1.0 towards 0.0 when the user pinches inward and increases from 1.0 when the user spreads fingers outward. |
| [int32_t OH_ArkUI_AxisEvent_GetAxisAction(const ArkUI_UIInputEvent* event)](#oh_arkui_axisevent_getaxisaction) | Obtains the action type of this axis event.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| [int32_t OH_ArkUI_AxisEvent_HasAxis(const ArkUI_UIInputEvent* event, int32_t axis)](#oh_arkui_axisevent_hasaxis) | Checks whether this axis event contains the specified axis type.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| [int32_t OH_ArkUI_PointerEvent_SetInterceptHitTestMode(const ArkUI_UIInputEvent* event, HitTestMode mode)](#oh_arkui_pointerevent_setintercepthittestmode) | Sets the touch test mode. This API only applies to scenarios raw input events are received, such as when **NODE_ON_TOUCH** is used for touch event handling. It cannot be used with **ArkUI_UIInputEvent** objects obtained from gesture events through [OH_ArkUI_GestureEvent_GetRawInputEvent](capi-native-gesture-h.md#oh_arkui_gestureevent_getrawinputevent).                                                                                                                                                                                                                                                                                                                                                                        |
| [int32_t OH_ArkUI_MouseEvent_GetMouseButton(const ArkUI_UIInputEvent* event)](#oh_arkui_mouseevent_getmousebutton) | Obtains the button type of a mouse event.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| [int32_t OH_ArkUI_MouseEvent_GetMouseAction(const ArkUI_UIInputEvent* event)](#oh_arkui_mouseevent_getmouseaction) | Obtains the action type of a mouse event.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| [int32_t OH_ArkUI_PointerEvent_SetStopPropagation(const ArkUI_UIInputEvent* event, bool stopPropagation)](#oh_arkui_pointerevent_setstoppropagation) | Sets whether to stop event propagation. This API only applies to scenarios raw input events are received, such as when **NODE_ON_TOUCH** is used for touch event handling, and does not apply to axis events. It cannot be used with **ArkUI_UIInputEvent** objects obtained from gesture events through [OH_ArkUI_GestureEvent_GetRawInputEvent](capi-native-gesture-h.md#oh_arkui_gestureevent_getrawinputevent). |
| [int32_t OH_ArkUI_UIInputEvent_GetDeviceId(const ArkUI_UIInputEvent* event)](#oh_arkui_uiinputevent_getdeviceid) | Obtains the device ID of the current UI input event.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| [int32_t OH_ArkUI_UIInputEvent_GetPressedKeys(const ArkUI_UIInputEvent* event, int32_t* pressedKeyCodes, int32_t* length)](#oh_arkui_uiinputevent_getpressedkeys) | Obtains all pressed keys. Currently, only key events are supported.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| [double OH_ArkUI_FocusAxisEvent_GetAxisValue(const ArkUI_UIInputEvent* event, int32_t axis)](#oh_arkui_focusaxisevent_getaxisvalue) | Obtains the axis value of a focus axis event.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| [int32_t OH_ArkUI_FocusAxisEvent_SetStopPropagation(const ArkUI_UIInputEvent* event, bool stopPropagation)](#oh_arkui_focusaxisevent_setstoppropagation) | Sets whether to prevent a focus axis event from bubbling up.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| [int32_t OH_ArkUI_UIInputEvent_GetModifierKeyStates(const ArkUI_UIInputEvent* event, uint64_t* keys)](#oh_arkui_uiinputevent_getmodifierkeystates) | Obtains the modifier key states for a UI input event. This API passes the states of all modifier keys through **keys** when the current event occurs. The application can perform a bitwise operation on keys and the modifier key types defined in [ArkUI_ModifierKeyName](capi-ui-input-event-h.md#arkui_modifierkeyname) to obtain the modifier keys that are pressed.                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| [int32_t OH_ArkUI_AxisEvent_SetPropagation(const ArkUI_UIInputEvent* event, bool propagation)](#oh_arkui_axisevent_setpropagation) | Sets whether to enable axis event bubbling. By default, axis events do not bubble and are only sent to the first component that can respond to axis events. You can enable axis event bubbling when an axis event is received to allow the event to be passed to the next ancestor component in the response chain that can handle axis events. This API cannot be used on axis events obtained from gesture events. |
| [int32_t OH_ArkUI_AxisEvent_GetScrollStep(const ArkUI_UIInputEvent* event)](#oh_arkui_axisevent_getscrollstep) | Obtains the scroll step coefficient for a wheel-based axis event. This value indicates the user-defined scroll step.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| [float OH_ArkUI_UIInputEvent_GetEventTargetWidth(const ArkUI_UIInputEvent* event)](#oh_arkui_uiinputevent_geteventtargetwidth) | Obtains the width of the component hit by an event.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| [float OH_ArkUI_UIInputEvent_GetEventTargetHeight(const ArkUI_UIInputEvent* event)](#oh_arkui_uiinputevent_geteventtargetheight) | Obtains the height of the component hit by an event.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| [float OH_ArkUI_UIInputEvent_GetEventTargetPositionX(const ArkUI_UIInputEvent* event)](#oh_arkui_uiinputevent_geteventtargetpositionx) | Obtains the x-coordinate of the component hit by an event.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| [float OH_ArkUI_UIInputEvent_GetEventTargetPositionY(const ArkUI_UIInputEvent* event)](#oh_arkui_uiinputevent_geteventtargetpositiony) | Obtains the y-coordinate of the component hit by an event.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| [float OH_ArkUI_UIInputEvent_GetEventTargetGlobalPositionX(const ArkUI_UIInputEvent* event)](#oh_arkui_uiinputevent_geteventtargetglobalpositionx) | Obtains the global x-coordinate of the component hit by an event.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| [float OH_ArkUI_UIInputEvent_GetEventTargetGlobalPositionY(const ArkUI_UIInputEvent* event)](#oh_arkui_uiinputevent_geteventtargetglobalpositiony) | Obtains the global y-coordinate of the component hit by an event.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| [int64_t OH_ArkUI_PointerEvent_GetPressedTimeByIndex(const ArkUI_UIInputEvent* event, uint32_t pointerIndex)](#oh_arkui_pointerevent_getpressedtimebyindex) | Obtains the press time of a specific touch point. This API is effective only for touch events.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| [float OH_ArkUI_MouseEvent_GetRawDeltaX(const ArkUI_UIInputEvent* event)](#oh_arkui_mouseevent_getrawdeltax) | Obtains the movement delta of the mouse along the X axis in a two-dimensional plane. The value is the original movement data of the mouse hardware, which is expressed in the unit of the mouse movement distance in the physical world. The reported value is determined by the hardware, not the physical or logical pixels of the screen.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| [float OH_ArkUI_MouseEvent_GetRawDeltaY(const ArkUI_UIInputEvent* event)](#oh_arkui_mouseevent_getrawdeltay) | Obtains the movement delta of the mouse along the Y axis in a two-dimensional plane. The value is the original movement data of the mouse hardware, which is expressed in the unit of the mouse movement distance in the physical world. The reported value is determined by the hardware, not the physical or logical pixels of the screen.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| [int32_t OH_ArkUI_MouseEvent_GetPressedButtons(const ArkUI_UIInputEvent* event, int32_t* pressedButtons, int32_t* length)](#oh_arkui_mouseevent_getpressedbuttons) | Obtains the pressed buttons from a mouse event.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| [int32_t OH_ArkUI_UIInputEvent_GetTargetDisplayId(const ArkUI_UIInputEvent* event)](#oh_arkui_uiinputevent_gettargetdisplayid) | Obtains the ID of the screen where the UI input event occurs.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| [bool OH_ArkUI_HoverEvent_IsHovered(const ArkUI_UIInputEvent* event)](#oh_arkui_hoverevent_ishovered) | Checks whether the cursor is hovering over this component.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| [int32_t OH_ArkUI_PointerEvent_CreateClonedEvent(const ArkUI_UIInputEvent* event, ArkUI_UIInputEvent** clonedEvent)](#oh_arkui_pointerevent_createclonedevent) | Creates a cloned event pointer based on an event pointer. This API is effective only for touch events.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| [int32_t OH_ArkUI_PointerEvent_DestroyClonedEvent(const ArkUI_UIInputEvent* event)](#oh_arkui_pointerevent_destroyclonedevent) | Destroys a cloned event pointer created by **OH_ArkUI_PointerEvent_CreateClonedEvent()**. After using a cloned event, call this API to release resources. |
| [int32_t OH_ArkUI_PointerEvent_SetClonedEventLocalPosition(const ArkUI_UIInputEvent* event, float x, float y)](#oh_arkui_pointerevent_setclonedeventlocalposition) | Sets the x-coordinate and y-coordinate of a cloned event relative to the upper left corner of the current component. This API should be used after a cloned event is created by calling **OH_ArkUI_PointerEvent_CreateClonedEvent()**. The **SetClonedEvent** APIs of the same series are applicable only to cloned events. |
| [int32_t OH_ArkUI_PointerEvent_SetClonedEventLocalPositionByIndex(const ArkUI_UIInputEvent* event, float x, float y, int32_t pointerIndex)](#oh_arkui_pointerevent_setclonedeventlocalpositionbyindex) | Sets the x-coordinate and y-coordinate of a specific contact point of a cloned event relative to the upper left corner of the current component. This API can be used only for the **ArkUI_UIInputEvent** cloned event pointer created by [OH_ArkUI_PointerEvent_CreateClonedEvent](#oh_arkui_pointerevent_createclonedevent). |
| [int32_t OH_ArkUI_PointerEvent_SetClonedEventActionType(const ArkUI_UIInputEvent* event, int32_t actionType)](#oh_arkui_pointerevent_setclonedeventactiontype) | Sets the action type of a cloned event.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| [int32_t OH_ArkUI_PointerEvent_SetClonedEventChangedFingerId(const ArkUI_UIInputEvent* event, int32_t fingerId)](#oh_arkui_pointerevent_setclonedeventchangedfingerid) | Sets the touch point ID of a cloned pointer event.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| [int32_t OH_ArkUI_PointerEvent_SetClonedEventFingerIdByIndex(const ArkUI_UIInputEvent* event, int32_t fingerId, int32_t pointerIndex)](#oh_arkui_pointerevent_setclonedeventfingeridbyindex) | Sets the touch point ID of a specific contact point of a cloned event.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| [int32_t OH_ArkUI_PointerEvent_PostClonedEvent(ArkUI_NodeHandle node, const ArkUI_UIInputEvent* event)](#oh_arkui_pointerevent_postclonedevent) | Posts a cloned event to a specific node.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| [ArkUI_ErrorCode OH_ArkUI_PointerEvent_CreateClonedPointerEvent(const ArkUI_UIInputEvent* event, ArkUI_UIInputEvent** clonedEvent)](#oh_arkui_pointerevent_createclonedpointerevent) | Creates a clone event for a specified event. This API applies to touch, mouse, and axis events.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| [ArkUI_ErrorCode OH_ArkUI_PointerEvent_CreatePointerEvent(ArkUI_UIInputEvent** event, ArkUI_UIInputEvent_Type type)](#oh_arkui_pointerevent_createpointerevent) | Creates a new event (not clone the existing event). This API applies to touch, mouse, and axis events.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| [ArkUI_ErrorCode OH_ArkUI_PointerEvent_DestroyClonedPointerEvent(const ArkUI_UIInputEvent* event)](#oh_arkui_pointerevent_destroyclonedpointerevent) | Destroys a cloned event pointer. This API applies to touch, mouse, and axis events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| [ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetActionType(const ArkUI_UIInputEvent* event, int32_t type)](#oh_arkui_clonedevent_setactiontype) | Sets an action type for a cloned event. This API applies to touch, mouse, and axis events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| [ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetSourceType(const ArkUI_UIInputEvent* event, int32_t sourceType)](#oh_arkui_clonedevent_setsourcetype) | Sets a source type for a cloned event. This API applies to touch, mouse, and axis events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| [ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetToolType(const ArkUI_UIInputEvent* event, int32_t toolType)](#oh_arkui_clonedevent_settooltype) | Sets a tool type for a cloned event. This API applies to touch, mouse, and axis events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| [ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetPressure(const ArkUI_UIInputEvent* event, float pressure)](#oh_arkui_clonedevent_setpressure) | Sets the pressure applied to a touchscreen for a cloned event. This API applies to touch events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| [ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetPressureByIndex(const ArkUI_UIInputEvent* event, float pressure, int32_t pointerIndex)](#oh_arkui_clonedevent_setpressurebyindex) | Sets the pressure applied to a touchscreen for a specific touch point in a cloned event. This API applies to touch events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| [ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetEventTime(const ArkUI_UIInputEvent* event, int64_t timestamp)](#oh_arkui_clonedevent_seteventtime) | Sets the time when a cloned UI input event occurs. This API applies to touch, mouse, and axis events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| [ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetDeviceId(const ArkUI_UIInputEvent* event, int32_t deviceId)](#oh_arkui_clonedevent_setdeviceid) | Sets the ID of the device that triggers a cloned UI input event. This API applies to touch, mouse, and axis events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| [ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetTargetDisplayId(const ArkUI_UIInputEvent* event, int32_t targetDisplayId)](#oh_arkui_clonedevent_settargetdisplayid) | Sets the ID of the display where a cloned UI input event occurs. This API applies to touch, mouse, and axis events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| [ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetChangedFingerId(const ArkUI_UIInputEvent* event, int32_t fingerId)](#oh_arkui_clonedevent_setchangedfingerid) | Sets the touch point ID for a cloned pointer event. This API applies to touch events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| [ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetFingerIdByIndex(const ArkUI_UIInputEvent* event, int32_t fingerId, int32_t pointerIndex)](#oh_arkui_clonedevent_setfingeridbyindex) | Sets the touch point ID of a specific contact point for a cloned event. This API applies to touch events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| [ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetChangedWindowPosition(const ArkUI_UIInputEvent* event, float x, float y)](#oh_arkui_clonedevent_setchangedwindowposition) | Sets the X-coordinate and Y-coordinate of a cloned event relative to the upper left corner of the current window. This API applies to touch, mouse, and axis events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| [ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetWindowPositionByIndex(const ArkUI_UIInputEvent* event, float x, float y, int32_t pointerIndex)](#oh_arkui_clonedevent_setwindowpositionbyindex) | Sets the X-coordinate and Y-coordinate of a specific contact point of a cloned event relative to the upper left corner of the current window. This API applies to touch events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| [ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetChangedScreenPosition(const ArkUI_UIInputEvent* event, float x, float y)](#oh_arkui_clonedevent_setchangedscreenposition) | Sets the X-coordinate and Y-coordinate of a cloned event relative to the upper left corner of the current screen. This API applies to touch, mouse, and axis events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| [ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetScreenPositionByIndex(const ArkUI_UIInputEvent* event, float x, float y, int32_t pointerIndex)](#oh_arkui_clonedevent_setscreenpositionbyindex) | Sets the X-coordinate and Y-coordinate of a specific contact point of a cloned event relative to the upper left corner of the current screen. This API applies to touch events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| [ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetChangedGlobalDisplayPosition(const ArkUI_UIInputEvent* event, float x, float y)](#oh_arkui_clonedevent_setchangedglobaldisplayposition) | Sets the coordinates for a cloned event in the [global coordinate system](../../windowmanager/window-terminology.md#global-coordinate-system). This API applies to touch events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| [ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetGlobalDisplayPositionByIndex(const ArkUI_UIInputEvent* event, float x, float y, int32_t pointerIndex)](#oh_arkui_clonedevent_setglobaldisplaypositionbyindex) | Sets the coordinates for a cloned event in the [global coordinate system](../../windowmanager/window-terminology.md#global-coordinate-system). This API applies to touch events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| [ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetHandleId(const ArkUI_UIInputEvent* event, int32_t eventHandleId)](#oh_arkui_clonedevent_sethandleid) | Sets the unique handle of an event processing session. This handle must be used for any further operations on the event. For a given finger, only one event with this handle is in the active state at a time. This API applies to touch, mouse, and axis events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| [ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetTiltAngle(const ArkUI_UIInputEvent* event, float tiltX, float tiltY)](#oh_arkui_clonedevent_settiltangle) | Sets the tilt angle of a cloned event relative to the YZ and XZ planes. The value range of **tiltX** is [-90, 90]. A positive value indicates a tilt to the right. The value range of **tiltY** is [-90, 90]. A positive value indicates a tilt downwards. This API applies to touch events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent). |
| [ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetRollAngle(const ArkUI_UIInputEvent* event, float rollAngle)](#oh_arkui_clonedevent_setrollangle) | Sets the rotation angle of the stylus around the Z-axis in a cloned event. This API applies to touch events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| [ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetPressedKeys(const ArkUI_UIInputEvent* event, int32_t* pressedKeyCodes, int32_t length)](#oh_arkui_clonedevent_setpressedkeys) | Sets all pressed keys in a cloned event. This API applies to touch, mouse, and axis events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| [ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetChangedTouchArea(const ArkUI_UIInputEvent* event, float width, float height)](#oh_arkui_clonedevent_setchangedtoucharea) | Sets the width and height of the finger contact area for a cloned event. This API applies to touch events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| [ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetTouchAreaByIndex(const ArkUI_UIInputEvent* event, float width, float height, int32_t pointerIndex)](#oh_arkui_clonedevent_settouchareabyindex) | Sets the width and height of the finger contact area for a specific contact point of a cloned event. This API applies to touch events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| [ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetChangedInteractionHand(const ArkUI_UIInputEvent* event, int32_t hand)](#oh_arkui_clonedevent_setchangedinteractionhand) | Sets whether a cloned event is triggered by the left or right hand. This API applies to touch events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| [ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetInteractionHandByIndex(const ArkUI_UIInputEvent* event, int32_t hand, int32_t pointerIndex)](#oh_arkui_clonedevent_setinteractionhandbyindex) | Sets whether a specific contact point of a cloned event is triggered by the left or right hand. This API applies to touch events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| [ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetPressedTimeByIndex(const ArkUI_UIInputEvent* event, int64_t pressedTime, int32_t pointerIndex)](#oh_arkui_clonedevent_setpressedtimebyindex) | Sets the time when a specific touch point is pressed in a cloned event. This API applies to touch events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| [ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetPinchAxisScaleValue(const ArkUI_UIInputEvent* event, double pinchAxisScaleValue)](#oh_arkui_clonedevent_setpinchaxisscalevalue) | Sets the pinch axis scaling value for a cloned event. This API applies to axis events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| [ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetHorizontalAxisScaleValue(const ArkUI_UIInputEvent* event, double horizontalAxisScaleValue)](#oh_arkui_clonedevent_sethorizontalaxisscalevalue) | Sets the horizontal axis scaling value for a cloned event. This API applies to axis events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| [ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetVerticalAxisScaleValue(const ArkUI_UIInputEvent* event, double verticalAxisScaleValue)](#oh_arkui_clonedevent_setverticalaxisscalevalue) | Sets the vertical axis scaling value for a cloned event. This API applies to axis events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| [ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetScrollStep(const ArkUI_UIInputEvent* event, int32_t scrollStep)](#oh_arkui_clonedevent_setscrollstep) | Sets the scrolling step coefficient for a cloned event. This API applies to axis events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| [ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetMouseButton(const ArkUI_UIInputEvent* event, int32_t button)](#oh_arkui_clonedevent_setmousebutton) | Sets a button type for a cloned event. This API applies to mouse events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent). |
| [ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetRawDeltaX(const ArkUI_UIInputEvent* event, float rawDeltaX)](#oh_arkui_clonedevent_setrawdeltax) | Sets the movement delta of the mouse along the x-axis in a two-dimensional plane. The value is the original movement data of the mouse hardware, which is expressed in the unit of the mouse movement distance in the physical world. This API applies to mouse events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| [ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetRawDeltaY(const ArkUI_UIInputEvent* event, float rawDeltaY)](#oh_arkui_clonedevent_setrawdeltay) | Sets the movement delta of the mouse along the y-axis in a two-dimensional plane. The value is the original movement data of the mouse hardware, which is expressed in the unit of the mouse movement distance in the physical world. This API applies to mouse events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| [ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetPressedButtons(const ArkUI_UIInputEvent* event, const int32_t* pressedButtons, int32_t length)](#oh_arkui_clonedevent_setpressedbuttons) | Sets the pressed keys in a cloned event. This API applies to mouse events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| [ArkUI_ErrorCode OH_ArkUI_PointerEvent_PostClonedEventWithStrategy(ArkUI_NodeHandle node, const ArkUI_UIInputEvent* event, ArkUI_CompetitionStrategy strategy)](#oh_arkui_pointerevent_postclonedeventwithstrategy) | Posts a cloned event to a specific node using a specified competition policy. This API is applicable to the scenario where a cloned event is injected to a target node and whether the injected event competes with the existing gestures on the target node needs to be controlled. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent). |
| [ArkUI_ErrorCode OH_ArkUI_UIInputEvent_GetLatestStatus()](#oh_arkui_uiinputevent_getlateststatus) | Obtains the result code of the most recent API call related to an **ArkUI_UIInputEvent** object. This API is typically unnecessary for normal operations, but can be used to check whether the most recent API call related to an **ArkUI_UIInputEvent** object is successful. |
| [ArkUI_CoastingAxisEvent* OH_ArkUI_UIInputEvent_GetCoastingAxisEvent(ArkUI_UIInputEvent* event)](#oh_arkui_uiinputevent_getcoastingaxisevent) | Obtains the coasting axis event from the specified component event. A valid event is available only when the user slides two fingers a certain distance on the touchpad and quickly releases them, and a component registered with the [NODE_ON_COASTING_AXIS_EVENT](capi-native-node-h.md#arkui_nodeeventtype) event exists at the pointer position. This API must be called after the [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md) object is obtained from the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object. The coasting axis event is triggered only when the user performs a two-finger swipe and releases on the touchpad, so it is exclusive to touchpad devices. This event generates axis values that gradually attenuate based on the initial swipe velocity after finger release. Due to factors such as refresh rate and performance constraints, the axis value of the current event may be higher or lower than the previous one. The following behavior will interrupt the coasting axis event and immediately trigger [ARKUI_COASTING_AXIS_EVENT_PHASE_END](#arkui_coastingaxiseventphase):1. Touching the touchpad2. Scrolling the mouse wheel3. Clicking a node registered for coasting axis events (clicking unregistered nodes has no effect). For example, if node A registers the event and node B is being scrolled during coasting, clicking node B will not interrupt the event. Click event interruption is affected by [OH_ArkUI_PointerEvent_SetInterceptHitTestMode](#oh_arkui_pointerevent_setintercepthittestmode). If the tapped area contains any nodes that can respond to coasting axis events, the coasting axis event will be forcibly terminated.4. Application hibernation (such as minimization and screen lock) |
| [int64_t OH_ArkUI_CoastingAxisEvent_GetEventTime(ArkUI_CoastingAxisEvent* event)](#oh_arkui_coastingaxisevent_geteventtime) | Obtains the time when a coasting axis event occurs.  |
| [ArkUI_CoastingAxisEventPhase OH_ArkUI_CoastingAxisEvent_GetPhase(ArkUI_CoastingAxisEvent* event)](#oh_arkui_coastingaxisevent_getphase) | Obtains the scroll phase of the specified coasting axis event.  |
| [float OH_ArkUI_CoastingAxisEvent_GetDeltaY(ArkUI_CoastingAxisEvent* event)](#oh_arkui_coastingaxisevent_getdeltay) | Obtains the vertical delta value of the specified coasting axis event. Unit: px, representing the single scroll increment (not the total scroll amount). Negative values indicate a downward direction (fingers swiping from top to bottom), and positive values indicate an upward direction (fingers swiping from bottom to top).  |
| [float OH_ArkUI_CoastingAxisEvent_GetDeltaX(ArkUI_CoastingAxisEvent* event)](#oh_arkui_coastingaxisevent_getdeltax) | Obtains the horizontal delta value of the specified coasting axis event. Unit: px, representing the single scroll increment (not the total scroll amount). Positive values indicate a rightward direction (fingers swiping from right to left), and negative values indicate a leftward direction (fingers swiping from left to right).  |
| [int32_t OH_ArkUI_CoastingAxisEvent_SetPropagation(ArkUI_CoastingAxisEvent* event, bool propagation)](#oh_arkui_coastingaxisevent_setpropagation) | Sets whether to enable event propagation for the specified coasting axis event. By default, event propagation is disabled.|
| [ArkUI_ErrorCode OH_ArkUI_TouchTestInfo_GetTouchTestInfoList(ArkUI_TouchTestInfo* info, ArkUI_TouchTestInfoItemArray* array, int32_t* size)](#oh_arkui_touchtestinfo_gettouchtestinfolist) | Obtains the array of touch test information items from the touch test information.|
| [float OH_ArkUI_TouchTestInfoItem_GetX(const ArkUI_TouchTestInfoItem* info)](#oh_arkui_touchtestinfoitem_getx) | Obtains the X coordinate relative to the upper left corner of the child component from the touch test information item, in px.|
| [float OH_ArkUI_TouchTestInfoItem_GetY(const ArkUI_TouchTestInfoItem* info)](#oh_arkui_touchtestinfoitem_gety) | Obtains the Y coordinate relative to the upper left corner of the child component from the touch test information item, in px.|
| [float OH_ArkUI_TouchTestInfoItem_GetWindowX(const ArkUI_TouchTestInfoItem* info)](#oh_arkui_touchtestinfoitem_getwindowx) | Obtains the X coordinate relative to the upper left corner of the current application window from the touch test information item, in px.|
| [float OH_ArkUI_TouchTestInfoItem_GetWindowY(const ArkUI_TouchTestInfoItem* info)](#oh_arkui_touchtestinfoitem_getwindowy) | Obtains the Y coordinate relative to the upper left corner of the current application window from the touch test information item, in px.|
| [float OH_ArkUI_TouchTestInfoItem_GetXRelativeToParent(const ArkUI_TouchTestInfoItem* info)](#oh_arkui_touchtestinfoitem_getxrelativetoparent) | Obtains the X coordinate relative to the upper left corner of the parent component from the touch test information item, in px.|
| [float OH_ArkUI_TouchTestInfoItem_GetYRelativeToParent(const ArkUI_TouchTestInfoItem* info)](#oh_arkui_touchtestinfoitem_getyrelativetoparent) | Obtains the Y coordinate relative to the upper left corner of the parent component from the touch test information item, in px.|
| [ArkUI_ErrorCode OH_ArkUI_TouchTestInfoItem_GetChildRect(const ArkUI_TouchTestInfoItem* info, ArkUI_Rect* childRect)](#oh_arkui_touchtestinfoitem_getchildrect) | Obtains the boundary rectangle information of the child component from the touch test information item.|
| [ArkUI_ErrorCode OH_ArkUI_TouchTestInfoItem_GetChildId(const ArkUI_TouchTestInfoItem* info, char* buffer, int32_t bufferSize)](#oh_arkui_touchtestinfoitem_getchildid) | Obtains the ID of the child component from the touch test information item.|
| [ArkUI_ErrorCode OH_ArkUI_TouchTestInfo_SetTouchResultStrategy(ArkUI_TouchTestInfo* info, ArkUI_TouchTestStrategy strategy)](#oh_arkui_touchtestinfo_settouchresultstrategy) | Sets the touch test policy, that is, the behavior of a component and its child components in a hit test. This API is applicable to scenarios where you want to customize the touch hit result, distribute touch events to a specified child component, or control whether sibling components continue to participate in the hit test. |
| [ArkUI_ErrorCode OH_ArkUI_TouchTestInfo_SetTouchResultId(ArkUI_TouchTestInfo* info, const char* id)](#oh_arkui_touchtestinfo_settouchresultid) | Sets the ID of the child component that needs to be involved in the hit test. This API is applicable to scenarios where you want to customize the touch test result and distribute touch events to a specified child component. |
| [int64_t OH_ArkUI_DigitalCrownEvent_GetEventTime(const ArkUI_UIInputEvent* event)](#oh_arkui_digitalcrownevent_geteventtime) | Obtains the time when a crown event occurs. The unit is ns. This API applies only when the input parameter **UIInputEvent** contains a crown event object. |
| [double OH_ArkUI_DigitalCrownEvent_GetAngularVelocity(const ArkUI_UIInputEvent* event)](#oh_arkui_digitalcrownevent_getangularvelocity) | Obtains the angular velocity at which a crown event occurs. The unit is °/s. This API applies only when the input parameter **UIInputEvent** contains a crown event object. |
| [double OH_ArkUI_DigitalCrownEvent_GetDegree(const ArkUI_UIInputEvent* event)](#oh_arkui_digitalcrownevent_getdegree) | Obtains the rotation angle at which a crown event occurs. The unit is °. This API applies only when the input parameter **UIInputEvent** contains a crown event object. |
| [ArkUI_CrownEvent_Action OH_ArkUI_DigitalCrownEvent_GetAction(const ArkUI_UIInputEvent* event)](#oh_arkui_digitalcrownevent_getaction) | Obtains the phase at which a crown event occurs. This API applies only when the input parameter **UIInputEvent** contains a crown event object. |
| [ArkUI_ErrorCode OH_ArkUI_DigitalCrownEvent_SetStopPropagation(const ArkUI_UIInputEvent* event, bool stopPropagation)](#oh_arkui_digitalcrownevent_setstoppropagation) | Sets whether to prevent event bubbling. This API is applicable when the current component has handled a crown event and does not want the event to be passed to its parent component or other ancestor components. This API applies only when the input parameter **UIInputEvent** contains a crown event object. |

## Enum Description

### ArkUI_UIInputEvent_Type

```c
enum ArkUI_UIInputEvent_Type
```

**Description**


Enumerates the UI input event types.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_UIINPUTEVENT_TYPE_UNKNOWN = 0 | Unknown.|
| ARKUI_UIINPUTEVENT_TYPE_TOUCH = 1 | Touch event.|
| ARKUI_UIINPUTEVENT_TYPE_AXIS = 2 | Axis event.|
| ARKUI_UIINPUTEVENT_TYPE_MOUSE = 3 | Mouse event.|
| ARKUI_UIINPUTEVENT_TYPE_KEY = 4 | Key event.<br>**Since**: 20|
| ARKUI_UIINPUTEVENT_TYPE_DIGITAL_CROWN = 5 | Crown event.<br>**Since**: 24|

### anonymous1

```c
enum anonymous1
```

**Description**


Enumerates the action types of the input event.

**Since**: 12

| Value| Description|
| -- | -- |
| UI_TOUCH_EVENT_ACTION_CANCEL = 0 | Cancellation of touch.|
| UI_TOUCH_EVENT_ACTION_DOWN = 1 | Pressing of touch.|
| UI_TOUCH_EVENT_ACTION_MOVE = 2 | Moving of touch.|
| UI_TOUCH_EVENT_ACTION_UP = 3 | Lifting of touch.|

### anonymous2

```c
enum anonymous2
```

**Description**


Enumerates the tool types of the input event.

**Since**: 12

| Value| Description|
| -- | -- |
| UI_INPUT_EVENT_TOOL_TYPE_UNKNOWN = 0 | Unknown tool type.|
| UI_INPUT_EVENT_TOOL_TYPE_FINGER = 1 | Finger.|
| UI_INPUT_EVENT_TOOL_TYPE_PEN = 2 | Stylus.|
| UI_INPUT_EVENT_TOOL_TYPE_MOUSE = 3 | Mouse.|
| UI_INPUT_EVENT_TOOL_TYPE_TOUCHPAD = 4 | Touchpad.|
| UI_INPUT_EVENT_TOOL_TYPE_JOYSTICK = 5 | Joystick.|

### anonymous3

```c
enum anonymous3
```

**Description**


Enumerates the source types of the input event.

**Since**: 12

| Value| Description|
| -- | -- |
| UI_INPUT_EVENT_SOURCE_TYPE_UNKNOWN = 0 | Unknown input source.|
| UI_INPUT_EVENT_SOURCE_TYPE_MOUSE = 1 | Mouse.|
| UI_INPUT_EVENT_SOURCE_TYPE_TOUCH_SCREEN = 2 | Touchscreen.|
| UI_INPUT_EVENT_SOURCE_TYPE_KEY = 4 | Key.<br>**Since**: 22|
| UI_INPUT_EVENT_SOURCE_TYPE_JOYSTICK = 5 | Joystick.<br>**Since**: 22|

### HitTestMode

```c
enum HitTestMode
```

**Description**


Enumerates the hit test modes.

**Since**: 12

| Value| Description|
| -- | -- |
| HTM_DEFAULT = 0 | Default hit test mode. The node itself and its child nodes respond to the hit test, but block the hit test of sibling nodes. It does not affect the hit test of ancestor nodes.|
| HTM_BLOCK = 1 | The node itself responds to the hit test and blocks the hit test of child nodes, sibling nodes, and ancestor nodes.|
| HTM_TRANSPARENT = 2 | Both the node itself and its child nodes respond to the hit test and do not block the hit test of sibling nodes and ancestor nodes.|
| HTM_NONE = 3 | The node itself does not respond to the hit test and does not block the hit test of child nodes, sibling nodes, and ancestor nodes.|
| HTM_BLOCK_HIERARCHY = 4 | The node itself and its child nodes respond to the hit test, preventing all sibling nodes and parent nodes with lower priority from participating in the hit test.<br>**Since**: 20|
| HTM_BLOCK_DESCENDANTS = 5 | The node itself does not respond to the hit test, and all its descendants (children, grandchildren, and more) also do not respond to the hit test. It does not affect the hit test of ancestor nodes.<br>**Since**: 20 |

### anonymous4

```c
enum anonymous4
```

**Description**


Enumerates the action types of the mouse event.

**Since**: 12

| Value| Description|
| -- | -- |
| UI_MOUSE_EVENT_ACTION_UNKNOWN = 0 | Unknown action.<br>Note: This action is processed by the system. You do not need to focus on it.|
| UI_MOUSE_EVENT_ACTION_PRESS = 1 | The mouse button is pressed.|
| UI_MOUSE_EVENT_ACTION_RELEASE = 2 | The mouse button is released.|
| UI_MOUSE_EVENT_ACTION_MOVE = 3 | The mouse cursor moves.|
| UI_MOUSE_EVENT_ACTION_CANCEL = 13 | The mouse button action is canceled.<br>**Since**: 18|

### anonymous5

```c
enum anonymous5
```

**Description**


Enumerates the button types of the mouse event.

**Since**: 12

| Value| Description|
| -- | -- |
| UI_MOUSE_EVENT_BUTTON_NONE = 0 | No button.|
| UI_MOUSE_EVENT_BUTTON_LEFT = 1 | Left button.|
| UI_MOUSE_EVENT_BUTTON_RIGHT = 2 | Right button.|
| UI_MOUSE_EVENT_BUTTON_MIDDLE = 3 | Middle button.|
| UI_MOUSE_EVENT_BUTTON_BACK = 4 | Back button on the left of the mouse.|
| UI_MOUSE_EVENT_BUTTON_FORWARD = 5 | Forward button on the left of the mouse.|

### ArkUI_ModifierKeyName

```c
enum ArkUI_ModifierKeyName
```

**Description**


Enumerates the modifier keys.

**Since**: 12

| Value| Description|
| -- | -- |
| ARKUI_MODIFIER_KEY_CTRL = 1 << 0 | Ctrl. |
| ARKUI_MODIFIER_KEY_SHIFT = 1 << 1 | Shift. |
| ARKUI_MODIFIER_KEY_ALT = 1 << 2 | Alt. |
| ARKUI_MODIFIER_KEY_FN = 1 << 3 | Fn (for debugging purposes only; typically, the Fn key state is not reported) |

### anonymous6

```c
enum anonymous6
```

**Description**


Defines the axis types of the [focus axis event](./arkui-ts/ts-universal-events-focus_axis.md).

**Since**: 15

| Value| Description|
| -- | -- |
| UI_FOCUS_AXIS_EVENT_ABS_X = 0 | Game controller X-axis.|
| UI_FOCUS_AXIS_EVENT_ABS_Y = 1 | Game controller Y-axis.|
| UI_FOCUS_AXIS_EVENT_ABS_Z = 2 | Game controller Z-axis.|
| UI_FOCUS_AXIS_EVENT_ABS_RZ = 3 | Game controller RZ-axis.|
| UI_FOCUS_AXIS_EVENT_ABS_GAS = 4 | Game controller GAS-axis.|
| UI_FOCUS_AXIS_EVENT_ABS_BRAKE = 5 | Game controller BRAKE-axis.|
| UI_FOCUS_AXIS_EVENT_ABS_HAT0X = 6 | Game controller HAT0X-axis.|
| UI_FOCUS_AXIS_EVENT_ABS_HAT0Y = 7 | Game controller HAT0Y-axis.|
| UI_FOCUS_AXIS_EVENT_ABS_RX = 8 | Game controller RX-axis.<br>**Since**: 23|
| UI_FOCUS_AXIS_EVENT_ABS_RY = 9 | Game controller RY-axis.<br>**Since**: 23|
| UI_FOCUS_AXIS_EVENT_ABS_THROTTLE = 10 | Game controller THROTTLE-axis.<br>**Since**: 23|
| UI_FOCUS_AXIS_EVENT_ABS_RUDDER = 11 | Game controller RUDDER-axis.<br>**Since**: 23|
| UI_FOCUS_AXIS_EVENT_ABS_WHEEL = 12 | Game controller WHEEL-axis.<br>**Since**: 23|
| UI_FOCUS_AXIS_EVENT_ABS_HAT1X = 13 | Game controller HAT1X-axis.<br>**Since**: 23|
| UI_FOCUS_AXIS_EVENT_ABS_HAT1Y = 14 | Game controller HAT1Y-axis.<br>**Since**: 23|
| UI_FOCUS_AXIS_EVENT_ABS_HAT2X = 15 | Game controller HAT2X-axis.<br>**Since**: 23|
| UI_FOCUS_AXIS_EVENT_ABS_HAT2Y = 16 | Game controller HAT2Y-axis.<br>**Since**: 23|
| UI_FOCUS_AXIS_EVENT_ABS_HAT3X = 17 | Game controller HAT3X-axis.<br>**Since**: 23|
| UI_FOCUS_AXIS_EVENT_ABS_HAT3Y = 18 | Game controller HAT3Y-axis.<br>**Since**: 23|

### ArkUI_InteractionHand

```c
enum ArkUI_InteractionHand
```

**Description**


Defines whether the touch event is from the left or right hand.

**Since**: 15

| Value| Description|
| -- | -- |
| ARKUI_EVENT_HAND_NONE = 0 | Unknown.|
| ARKUI_EVENT_HAND_LEFT = 1 | Left hand.|
| ARKUI_EVENT_HAND_RIGHT = 2 | Right hand.|

### anonymous7

```c
enum anonymous7
```

**Description**


Defines the action types of the [axis event](./arkui-ts/ts-universal-events-axis.md).

**Since**: 15

| Value| Description|
| -- | -- |
| UI_AXIS_EVENT_ACTION_NONE = 0 | The axis event is abnormal.|
| UI_AXIS_EVENT_ACTION_BEGIN = 1 | The axis event begins.|
| UI_AXIS_EVENT_ACTION_UPDATE = 2 | The axis event is updated.|
| UI_AXIS_EVENT_ACTION_END = 3 | The axis event ends.|
| UI_AXIS_EVENT_ACTION_CANCEL = 4 | The axis event is canceled.|

### anonymous8

```c
enum anonymous8
```

**Description**


Enumerates the axis types for axis events.

**Since**: 22

| Value| Description|
| -- | -- |
| UI_AXIS_TYPE_VERTICAL_AXIS = 0 | Vertical axis.|
| UI_AXIS_TYPE_HORIZONTAL_AXIS = 1 | Horizontal axis.|
| UI_AXIS_TYPE_PINCH_AXIS = 2 | Pinch axis.|

### ArkUI_CoastingAxisEventPhase

```c
enum ArkUI_CoastingAxisEventPhase
```

**Description**


Enumerates the phases of coasting axis events.

**Since**: 22

| Value| Description|
| -- | -- |
| ARKUI_COASTING_AXIS_EVENT_PHASE_NONE = 0 | Invalid coasting axis event phase, serving as an abnormal default value. You can verify that the coasting axis phase is not this value to confirm event validity. |
| ARKUI_COASTING_AXIS_EVENT_PHASE_BEGIN = 1 | The coasting axis event begins. This is the initial event in the coasting phase. |
| ARKUI_COASTING_AXIS_EVENT_PHASE_UPDATE = 2 | The coasting axis event updates. In this phase, you can obtain the coasting axis delta value to handle scroll offset calculations. |
| ARKUI_COASTING_AXIS_EVENT_PHASE_END = 3 | The coasting axis event ends. This phase is triggered when coasting stops due to braking (for example, the user re-engages the touchpad during coasting, or interacts via a mouse or touchscreen) or natural decay to rest. Upon reaching this phase, immediately terminate the coasting scroll effect. |

### ArkUI_TouchTestStrategy

```c
enum ArkUI_TouchTestStrategy
```

**Description**


Defines the touch test policy.

**Since**: 22

| Value| Description|
| -- | -- |
| ARKUI_TOUCH_TEST_STRATEGY_DEFAULT = 0 | Custom dispatch has no effect. The system dispatches events based on the hit status of the current node. |
| ARKUI_TOUCH_TEST_STRATEGY_FORWARD_COMPETITION = 1 | The event is dispatched to a specified child node, and the system determines whether to dispatch events to other sibling nodes. |
| ARKUI_TOUCH_TEST_STRATEGY_FORWARD = 2 | The event is dispatched to a specified child node, and the system will not dispatch events to other sibling nodes. |

### ArkUI_CompetitionStrategy

```c
enum ArkUI_CompetitionStrategy
```

**Description**


Strategy that determines whether the gesture identification result between the event injector and the injected end is in a competition scenario. This strategy determines how the event injector interacts with the gesture processing logic of the injected end. In non-competition scenarios, the gestures of the two parties are triggered simultaneously. In competition scenarios, only the gesture of one party is triggered.

**Since**: 24

| Value| Description|
| -- | -- |
| ARKUI_COMPETITION_STRATEGY_DEFAULT = 0 | Non-competition strategy. The injected event does not compete with any existing gesture. The injected event and existing gestures can be processed independently and concurrently. |
| ARKUI_COMPETITION_STRATEGY_COMPETITION = 1 | Competition strategy The gestures between the event injector and the injected end are in competition, and only the gestures of one party can be processed. |

### ArkUI_CrownEvent_Action

```c
enum ArkUI_CrownEvent_Action
```

**Description**


Defines the phases of a crown event.

**Since**: 24

| Value| Description|
| -- | -- |
| ARKUI_CROWNEVENT_ACTION_UNKNOWN = 0 | Unknown phase of the crown event. |
| ARKUI_CROWNEVENT_ACTION_UPDATE = 1 | The crown event is updated. |
| ARKUI_CROWNEVENT_ACTION_END = 2 | The crown event ends. |

## Function Description

### OH_ArkUI_UIInputEvent_GetType()

```c
int32_t OH_ArkUI_UIInputEvent_GetType(const ArkUI_UIInputEvent* event)
```

**Description**


Obtains the type of a UI input event. Before accessing an **ArkUI_UIInputEvent** pointer, use this API to determine the type of the input event. This API returns a value from the [ArkUI_UIInputEvent_Type](capi-ui-input-event-h.md#arkui_uiinputevent_type) enum. For example, if the event is a touch event, which is directional, you can use **OH_ArkUI_UIInputEvent_GetXXX** and **OH_ArkUI_PointerEvent_GetXXX** for access. Using **OH_ArkUI_KeyEvent_GetXXX** to access the event may produce an invalid return value. For unsupported event types, this API returns the default value **0**.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Type of the UI input event. Returns **0** if any parameter error occurs.|

### OH_ArkUI_UIInputEvent_GetAction()

```c
int32_t OH_ArkUI_UIInputEvent_GetAction(const ArkUI_UIInputEvent* event)
```

**Description**


Obtains the action type of an input event. The action type defines the phase of a basic event (for example, start or end) and characterizes its behavior, such as touch down or touch up. Action types are specific to the event category: [UI_TOUCH_EVENT_ACTION](#anonymous1) for touch events and [UI_MOUSE_EVENT_ACTION](#anonymous4) for mouse events. For axis events, use [OH_ArkUI_AxisEvent_GetAxisAction](#oh_arkui_axisevent_getaxisaction) to obtain the action type, which returns [UI_AXIS_EVENT_ACTION](#anonymous7). For key events, use [OH_ArkUI_KeyEvent_GetType](./capi-native-key-event-h.md#oh_arkui_keyevent_gettype) to obtain the action type, which returns [ArkUI_KeyEventType](./capi-native-key-event-h.md#arkui_keyeventtype).

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Action type of the UI input event. Returns **-1** if any parameter error occurs.|

### OH_ArkUI_UIInputEvent_GetSourceType()

```c
int32_t OH_ArkUI_UIInputEvent_GetSourceType(const ArkUI_UIInputEvent* event)
```

**Description**


Obtains the source type of a UI input event. The source represents the physical device, such as a touchscreen or mouse device, that generates the input event. It is defined by [UI_INPUT_EVENT_SOURCE_TYPE](#anonymous3). This is different from the input tool, which is the device used to interact with the source, for example, a finger or stylus. For example, a mouse device acts as both the source and tool for click events. For key events, obtaining the source type is not supported, and in such cases, the API will return an **unknown** value.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Source type of the UI input event.|

### OH_ArkUI_UIInputEvent_GetToolType()

```c
int32_t OH_ArkUI_UIInputEvent_GetToolType(const ArkUI_UIInputEvent* event)
```

**Description**


Obtains the tool type of a UI input event. The input tool is a tool that operates an input source device to generate an event, such as a finger or a stylus pen. The input tool does not directly generate events but can drive the input source device to continuously generate events. The return type is defined in the [UI_INPUT_EVENT_TOOL_TYPE](#anonymous2) enumeration. For key events, obtaining the tool type is not supported, and in such cases, the API will return an **unknown** value.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Tool type of the UI input event.|

### OH_ArkUI_UIInputEvent_GetEventTime()

```c
int64_t OH_ArkUI_UIInputEvent_GetEventTime(const ArkUI_UIInputEvent* event)
```

**Description**


Obtains the time when a specified UI input event occurs. The unit is ns.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|

**Return value**

| Type| Description|
| -- | -- |
| int64_t | Time when the UI input event occurs. Returns **0** if any parameter error occurs.|

### OH_ArkUI_PointerEvent_GetPointerCount()

```c
uint32_t OH_ArkUI_PointerEvent_GetPointerCount(const ArkUI_UIInputEvent* event)
```

**Description**


Obtains the number of contact points from a pointer event (such as a touch, mouse, or axis event). Pointer events are typically events that carry position information, such as touch events, where the location of the event can be determined. Non-pointer events, such as key events, do not have position information and do not involve points, so this API always returns **0**. For touch events, this API returns the number of active touch points, for example, fingers on the screen. For mouse and axis events, this API always returns **1**, as they are single-pointer interactions.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|

**Return value**

| Type| Description|
| -- | -- |
| uint32_t | Number of contact points in the pointer event.|

### OH_ArkUI_PointerEvent_GetPointerId()

```c
int32_t OH_ArkUI_PointerEvent_GetPointerId(const ArkUI_UIInputEvent* event, uint32_t pointerIndex)
```

**Description**


Obtains the unique ID of a contact point from a pointer event (such as a touch, mouse, or axis event). The ID distinguishes between multiple touch points from the same input device. The return value itself does not have any other meaning beyond identifying the touch point.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|
| uint32_t pointerIndex | Index of the target touch point in the multi-touch data list. The valid value range is [0, OH_ArkUI_PointerEvent_GetPointerCount(event) – 1]. If the value is out of range, an abnormal parameter result is returned. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Unique ID of the specific contact point.|

### OH_ArkUI_PointerEvent_GetChangedPointerId()

```c
int32_t OH_ArkUI_PointerEvent_GetChangedPointerId(const ArkUI_UIInputEvent* event, uint32_t* pointerIndex)
```

**Description**


Obtains the finger ID that triggers the current event.

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|
| uint32_t* pointerIndex | Pointer to the output parameter, which is used to receive the index of the touch point that triggers the current event in the multi-touch data list. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_PointerEvent_GetX()

```c
float OH_ArkUI_PointerEvent_GetX(const ArkUI_UIInputEvent* event)
```

**Description**


Obtains the x-coordinate relative to the upper left corner of the current component from a pointer event (such as a touch, mouse, or axis event).

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|

**Return value**

| Type| Description|
| -- | -- |
| float | X-coordinate of the current pointer event relative to the upper left corner of the current component. The default unit is vp. The unit can vary according to the [setLengthMetricUnit](../apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setlengthmetricunit) setting. Returns **0.0f** if a parameter error occurs. |

### OH_ArkUI_PointerEvent_GetXByIndex()

```c
float OH_ArkUI_PointerEvent_GetXByIndex(const ArkUI_UIInputEvent* event, uint32_t pointerIndex)
```

**Description**


Obtains the x-coordinate of a specific contact point relative to the upper left corner of the current component from a pointer event (such as a touch, mouse, or axis event). For mouse and axis events, this API returns the default value of **0.0f** if the given index is greater than 0.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|
| uint32_t pointerIndex | Index of the target touch point in the multi-touch data list. For mouse and axis events, the default value **0.0f** is returned if the value of this parameter is greater than 0. |

**Return value**

| Type| Description|
| -- | -- |
| float | X-coordinate of a specific touch point in the pointer event relative to the upper left corner of the current component. The default unit is vp. The unit can vary according to the [setLengthMetricUnit](../apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setlengthmetricunit) setting. Returns **0.0f** if a parameter error occurs. |

### OH_ArkUI_PointerEvent_GetY()

```c
float OH_ArkUI_PointerEvent_GetY(const ArkUI_UIInputEvent* event)
```

**Description**


Obtains the y-coordinate relative to the upper left corner of the current component from a pointer event (such as a touch, mouse, or axis event).

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|

**Return value**

| Type| Description|
| -- | -- |
| float | Y-coordinate of the current pointer event relative to the upper left corner of the current component. The default unit is vp. The unit can vary according to the [setLengthMetricUnit](../apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setlengthmetricunit) setting. Returns **0.0f** if a parameter error occurs. |

### OH_ArkUI_PointerEvent_GetYByIndex()

```c
float OH_ArkUI_PointerEvent_GetYByIndex(const ArkUI_UIInputEvent* event, uint32_t pointerIndex)
```

**Description**


Obtains the y-coordinate of a specific contact point relative to the upper left corner of the current component from a pointer event (such as a touch, mouse, or axis event). For mouse and axis events, this API returns the default value of **0.0f** if the given index is greater than 0.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|
| uint32_t pointerIndex | Index in the multi-touch data list. For mouse and axis events, only index 0 is supported. If an index greater than 0 is passed, **0.0f** is returned. For touch events, if an index beyond the valid range is passed, **0.0f** is returned. |

**Return value**

| Type| Description|
| -- | -- |
| float | Y-coordinate of a specific touch point in the pointer event relative to the upper left corner of the current component. The default unit is vp. The unit can vary according to the [setLengthMetricUnit](../apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setlengthmetricunit) setting. Returns **0.0f** if a parameter error occurs. |

### OH_ArkUI_PointerEvent_GetCurrentLocalX()

```c
float OH_ArkUI_PointerEvent_GetCurrentLocalX(const ArkUI_UIInputEvent* event)
```

**Description**


Obtains the X coordinate relative to the upper left corner of the current component from a [pointer event](../../ui/arkts-interaction-capability-overview.md#pointer-event)(such as a touch event, mouse event, or axis event) based on the real-time location.

**Since:** 26.0.0


**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|

**Return value**

| Type| Description|
| -- | -- |
| float | X-coordinate of the current pointer event relative to the upper left corner of the current component. The default unit is vp. The unit can vary according to the [setLengthMetricUnit](../apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setlengthmetricunit) setting. Returns **0.0f** if a parameter error occurs. |

### OH_ArkUI_PointerEvent_GetCurrentLocalXByIndex()

```c
float OH_ArkUI_PointerEvent_GetCurrentLocalXByIndex(const ArkUI_UIInputEvent* event, uint32_t pointerIndex)
```

**Description**


Obtains the X coordinate of a specific contact point relative to the upper left corner of the current component from a [pointer event](../../ui/arkts-interaction-capability-overview.md#pointer-event)(such as a touch event, mouse event, or axis event) based on the real-time location.

The value of **pointerIndex** is of the **uint32_t** type and cannot be less than 0. If the index exceeds the range of touch points supported by the current event, the value is invalid.

For mouse and axis events, an index value other than 0 is considered invalid.

For touch events, this API is used to obtain the X coordinate of a specific contact point relative to the upper left corner of the current component based on the given index.

**Since:** 26.0.0


**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|
| uint32_t pointerIndex | Index of the target touch point in the multi-touch data list. For mouse and axis events, this parameter must be set to **0**. |

**Return value**

| Type| Description|
| -- | -- |
| float | X-coordinate of a specific touch point relative to the upper left corner of the current component. The default unit is vp. The unit can vary according to the [setLengthMetricUnit](../apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setlengthmetricunit) setting. Returns **0.0f** if a parameter error occurs. |

### OH_ArkUI_PointerEvent_GetCurrentLocalY()

```c
float OH_ArkUI_PointerEvent_GetCurrentLocalY(const ArkUI_UIInputEvent* event)
```

**Description**


Obtains the Y coordinate relative to the upper left corner of the current component from a [pointer event](../../ui/arkts-interaction-capability-overview.md#pointer-event)(such as a touch event, mouse event, or axis event) based on the real-time location.

**Since:** 26.0.0


**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|

**Return value**

| Type| Description|
| -- | -- |
| float | Y-coordinate of the current pointer event relative to the upper left corner of the current component. The default unit is vp. The unit can vary according to the [setLengthMetricUnit](../apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setlengthmetricunit) setting. Returns **0.0f** if a parameter error occurs. |

### OH_ArkUI_PointerEvent_GetCurrentLocalYByIndex()

```c
float OH_ArkUI_PointerEvent_GetCurrentLocalYByIndex(const ArkUI_UIInputEvent* event, uint32_t pointerIndex)
```

**Description**


Obtains the Y coordinate of a specific contact point relative to the upper left corner of the current component from a [pointer event](../../ui/arkts-interaction-capability-overview.md#pointer-event)(such as a touch event, mouse event, or axis event) based on the real-time location.

The value of **pointerIndex** is of the **uint32_t** type and cannot be less than 0. If the index exceeds the range of touch points supported by the current event, the value is invalid.

For mouse and axis events, an index value other than 0 is considered invalid.

For touch events, this API is used to obtain the Y coordinate of a specific contact point relative to the upper left corner of the current component based on the given index.

**Since:** 26.0.0


**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|
| uint32_t pointerIndex | Index of the target touch point in the multi-touch data list. For mouse and axis events, this parameter must be set to **0**. |

**Return value**

| Type| Description|
| -- | -- |
| float | Y-coordinate of a specific touch point relative to the upper left corner of the current component. The default unit is vp. The unit can vary according to the [setLengthMetricUnit](../apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setlengthmetricunit) setting. Returns **0.0f** if a parameter error occurs. |

### OH_ArkUI_PointerEvent_GetWindowX()

```c
float OH_ArkUI_PointerEvent_GetWindowX(const ArkUI_UIInputEvent* event)
```

**Description**


Obtains the x-coordinate relative to the upper left corner of the current application window from a pointer event (such as a touch, mouse, or axis event).

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|

**Return value**

| Type| Description|
| -- | -- |
| float | X-coordinate of the current pointer event relative to the upper left corner of the current application window. The default unit is vp. The unit can vary according to the [setLengthMetricUnit](../apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setlengthmetricunit) setting. Returns **0.0f** if a parameter error occurs. |

### OH_ArkUI_PointerEvent_GetWindowXByIndex()

```c
float OH_ArkUI_PointerEvent_GetWindowXByIndex(const ArkUI_UIInputEvent* event, uint32_t pointerIndex)
```

**Description**


Obtains the x-coordinate of a specific contact point relative to the upper left corner of the current application window from a pointer event (such as a touch, mouse, or axis event). For mouse and axis events, this API returns the default value of **0.0f** if the given index is greater than 0.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|
| uint32_t pointerIndex | Index in the multi-touch data list. For mouse and axis events, only index 0 is supported. If an index greater than 0 is passed, **0.0f** is returned. For touch events, if an index beyond the valid range is passed, **0.0f** is returned. |

**Return value**

| Type| Description|
| -- | -- |
| float | X-coordinate of a specific touch point in the pointer event relative to the upper left corner of the current application window. The default unit is vp. The unit can vary according to the [setLengthMetricUnit](../apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setlengthmetricunit) setting. Returns **0.0f** if a parameter error occurs. |

### OH_ArkUI_PointerEvent_GetWindowY()

```c
float OH_ArkUI_PointerEvent_GetWindowY(const ArkUI_UIInputEvent* event)
```

**Description**


Obtains the y-coordinate relative to the upper left corner of the current application window from a pointer event (such as a touch, mouse, or axis event).

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|

**Return value**

| Type| Description|
| -- | -- |
| float | Y-coordinate of the current pointer event relative to the upper left corner of the current application window. The default unit is vp. The unit can vary according to the [setLengthMetricUnit](../apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setlengthmetricunit) setting. Returns **0.0f** if a parameter error occurs. |

### OH_ArkUI_PointerEvent_GetWindowYByIndex()

```c
float OH_ArkUI_PointerEvent_GetWindowYByIndex(const ArkUI_UIInputEvent* event, uint32_t pointerIndex)
```

**Description**


Obtains the y-coordinate of a specific contact point relative to the upper left corner of the current application window from a pointer event (such as a touch, mouse, or axis event). For mouse and axis events, this API returns the default value of **0.0f** if the given index is greater than 0.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|
| uint32_t pointerIndex | Index in the multi-touch data list. For mouse and axis events, only index 0 is supported. If an index greater than 0 is passed, **0.0f** is returned. For touch events, if an index beyond the valid range is passed, **0.0f** is returned. |

**Return value**

| Type| Description|
| -- | -- |
| float | Y-coordinate of a specific touch point in the pointer event relative to the upper left corner of the current application window. The default unit is vp. The unit can vary according to the [setLengthMetricUnit](../apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setlengthmetricunit) setting. Returns **0.0f** if a parameter error occurs. |

### OH_ArkUI_PointerEvent_GetDisplayX()

```c
float OH_ArkUI_PointerEvent_GetDisplayX(const ArkUI_UIInputEvent* event)
```

**Description**


Obtains the x-coordinate relative to the upper left corner of the current screen from a pointer event (such as a touch, mouse, or axis event).

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|

**Return value**

| Type| Description|
| -- | -- |
| float | X-coordinate of the current pointer event relative to the upper left corner of the current display. The default unit is vp. The unit can vary according to the [setLengthMetricUnit](../apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setlengthmetricunit) setting. Returns **0.0f** if a parameter error occurs. |

### OH_ArkUI_PointerEvent_GetDisplayXByIndex()

```c
float OH_ArkUI_PointerEvent_GetDisplayXByIndex(const ArkUI_UIInputEvent* event, uint32_t pointerIndex)
```

**Description**


Obtains the x-coordinate of a specific contact point relative to the upper left corner of the current screen from a pointer event (such as a touch, mouse, or axis event). For mouse and axis events, this API returns the default value of **0.0f** if the given index is greater than 0.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|
| uint32_t pointerIndex | Index in the multi-touch data list. For mouse and axis events, only index 0 is supported. If an index greater than 0 is passed, **0.0f** is returned. For touch events, if an index beyond the valid range is passed, **0.0f** is returned. |

**Return value**

| Type| Description|
| -- | -- |
| float | X-coordinate of a specific touch point in the pointer event relative to the upper left corner of the current display. The default unit is vp. The unit can vary according to the [setLengthMetricUnit](../apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setlengthmetricunit) setting. Returns **0.0f** if a parameter error occurs. |

### OH_ArkUI_PointerEvent_GetDisplayY()

```c
float OH_ArkUI_PointerEvent_GetDisplayY(const ArkUI_UIInputEvent* event)
```

**Description**


Obtains the y-coordinate relative to the upper left corner of the current screen from a pointer event (such as a touch, mouse, or axis event).

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|

**Return value**

| Type| Description|
| -- | -- |
| float | Y-coordinate of the current pointer event relative to the upper left corner of the current display. The default unit is vp. The unit can vary according to the [setLengthMetricUnit](../apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setlengthmetricunit) setting. Returns **0.0f** if a parameter error occurs. |

### OH_ArkUI_PointerEvent_GetDisplayYByIndex()

```c
float OH_ArkUI_PointerEvent_GetDisplayYByIndex(const ArkUI_UIInputEvent* event, uint32_t pointerIndex)
```

**Description**


Obtains the y-coordinate of a specific contact point relative to the upper left corner of the current screen from a pointer event (such as a touch, mouse, or axis event). For mouse and axis events, this API returns the default value of **0.0f** if the given index is greater than 0.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|
| uint32_t pointerIndex | Index in the multi-touch data list. For mouse and axis events, only index 0 is supported. If an index greater than 0 is passed, **0.0f** is returned. For touch events, if an index beyond the valid range is passed, **0.0f** is returned. |

**Return value**

| Type| Description|
| -- | -- |
| float | Y-coordinate of a specific touch point in the pointer event relative to the upper left corner of the current display. The default unit is vp. The unit can vary according to the [setLengthMetricUnit](../apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setlengthmetricunit) setting. Returns **0.0f** if a parameter error occurs. |

### OH_ArkUI_PointerEvent_GetGlobalDisplayX()

```c
float OH_ArkUI_PointerEvent_GetGlobalDisplayX(const ArkUI_UIInputEvent* event)
```

**Description**


Obtains the x-coordinate relative to the global display from a pointer event (such as a touch, mouse, or axis event). The position information can be obtained only from a [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md) event.

**Since**: 20


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|

**Return value**

| Type| Description|
| -- | -- |
| float | X-coordinate relative to the global display. The default unit is vp. The unit can vary according to the [setLengthMetricUnit](../apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setlengthmetricunit) setting. **0.0f** is returned if any parameter error occurs (for example, if the event does not contain position information). |

### OH_ArkUI_PointerEvent_GetGlobalDisplayXByIndex()

```c
float OH_ArkUI_PointerEvent_GetGlobalDisplayXByIndex(const ArkUI_UIInputEvent* event, uint32_t pointerIndex)
```

**Description**


Obtains the x-coordinate relative to the global display from a pointer event (such as a touch, mouse, or axis event). Position information can only be obtained from pointer events. For mouse and axis events, if the provided **pointerIndex** is greater than 0, this API always returns the default value **0.0f**.

**Since**: 20


**Parameters**

| Name| Description                                                                                                                 |
| -- |---------------------------------------------------------------------------------------------------------------------|
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.                                                                                                   |
| uint32_t pointerIndex | Index of the target touch point in the multi-touch data list. The valid value range is [0, [OH_ArkUI_PointerEvent_GetPointerCount()](#oh_arkui_pointerevent_getpointercount) – 1]. For mouse and axis events, this parameter must be set to **0**. |

**Return value**

| Type| Description|
| -- | -- |
| float | X-coordinate of a specific touch point in the pointer event relative to the global display. The default unit is vp. The unit can vary according to the [setLengthMetricUnit](../apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setlengthmetricunit) setting. Returns **0.0f** if any parameter error occurs. |

### OH_ArkUI_PointerEvent_GetGlobalDisplayY()

```c
float OH_ArkUI_PointerEvent_GetGlobalDisplayY(const ArkUI_UIInputEvent* event)
```

**Description**


Obtains the y-coordinate relative to the global display from a pointer event (such as a touch, mouse, or axis event). The position information can be obtained only from a [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md) event.

**Since**: 20


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|

**Return value**

| Type| Description|
| -- | -- |
| float | Y-coordinate relative to the global display. The default unit is vp. The unit can vary according to the [setLengthMetricUnit](../apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setlengthmetricunit) setting. **0.0f** is returned if any parameter error occurs (for example, if the event does not contain position information). |

### OH_ArkUI_PointerEvent_GetGlobalDisplayYByIndex()

```c
float OH_ArkUI_PointerEvent_GetGlobalDisplayYByIndex(const ArkUI_UIInputEvent* event, uint32_t pointerIndex)
```

**Description**


Obtains the y-coordinate relative to the global display from a pointer event (such as a touch, mouse, or axis event). Position information can only be obtained from pointer events. For mouse and axis events, if the provided **pointerIndex** is greater than 0, this API always returns the default value **0.0f**.

**Since**: 20


**Parameters**

| Name| Description                                                                                 |
| -- |-------------------------------------------------------------------------------------|
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.                                                                   |
| uint32_t pointerIndex | Index of the target touch point in the multi-touch data list. The valid value range is [0, [OH_ArkUI_PointerEvent_GetPointerCount()](#oh_arkui_pointerevent_getpointercount) – 1]. For mouse and axis events, this parameter must be set to **0**. |

**Return value**

| Type| Description|
| -- | -- |
| float | Y-coordinate relative to the global display. The default unit is vp. The unit can vary according to the [setLengthMetricUnit](../apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setlengthmetricunit) setting. Returns **0.0f** if any parameter error occurs. |

### OH_ArkUI_PointerEvent_GetPressure()

```c
float OH_ArkUI_PointerEvent_GetPressure(const ArkUI_UIInputEvent* event, uint32_t pointerIndex)
```

**Description**


Obtains the pressure applied to the touchscreen from a pointer event (such as a touch event). This API is applicable to scenarios where the brush thickness or interaction effect needs to be adjusted based on the touch pressure, such as drawing and writing.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|
| uint32_t pointerIndex | Index of the target touch point in the multi-touch data list. The valid value range is [0, OH_ArkUI_PointerEvent_GetPointerCount(event) – 1]. If the value is out of range, the default value **0.0f** is returned. |

**Return value**

| Type| Description|
| -- | -- |
| float | Touch pressure generated by the current pointer event. The value range is [0, 1]. The pressure is positively correlated with the value. If the parameter is abnormal, the default value **0.0f** is returned. The hardware parameter configuration may vary depending on the device. On some devices, the return value may be greater than 1. |

### OH_ArkUI_PointerEvent_GetTiltX()

```c
float OH_ArkUI_PointerEvent_GetTiltX(const ArkUI_UIInputEvent* event, uint32_t pointerIndex)
```

**Description**


Obtains the tilt relative to the YZ plane from a pointer event (such as a touch event). This API is applicable to scenarios where the brush effect needs to be adjusted based on the tilt direction of the stylus pen, such as drawing and writing. The value range is [–90, 90], in degrees. A positive value indicates a tilt to the right. This API is applicable only to stylus-based touch events from devices that support tilt angle reporting.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|
| uint32_t pointerIndex | Index of the target touch point in the multi-touch data list. The valid value range is [0, OH_ArkUI_PointerEvent_GetPointerCount(event) – 1]. If the value is out of range, an abnormal parameter result is returned. |

**Return value**

| Type| Description|
| -- | -- |
| float | Angle relative to the YZ plane.|

### OH_ArkUI_PointerEvent_GetTiltY()

```c
float OH_ArkUI_PointerEvent_GetTiltY(const ArkUI_UIInputEvent* event, uint32_t pointerIndex)
```

**Description**


Obtains the angle relative to the XZ plane from a pointer event (for example, a touch event). The value range is [-90, 90], in deg. A positive value indicates a downward tilt. This API is applicable only to stylus-based touch events from devices that support tilt angle reporting.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|
| uint32_t pointerIndex | Index of the target touch point in the multi-touch data list. The valid value range is [0, OH_ArkUI_PointerEvent_GetPointerCount(event) – 1]. |

**Return value**

| Type| Description|
| -- | -- |
| float | Angle relative to the XZ plane.|

### OH_ArkUI_PointerEvent_GetRollAngle()

```c
int32_t OH_ArkUI_PointerEvent_GetRollAngle(const ArkUI_UIInputEvent* event, double* rollAngle)
```

**Description**


Obtains the rotation angle of the stylus pen around the z-axis. This API is applicable to scenarios where the brush direction or interaction effect needs to be adjusted based on the rotation direction of the stylus pen, such as drawing and writing.

**Since**: 17


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the current UI input event.|
| double* rollAngle | Rotation angle of the stylus around the z-axis, in deg.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. The possible cause is that the event pointer or the output parameter **rollAngle** is invalid. Check and pass a valid parameter. |

### OH_ArkUI_PointerEvent_GetTouchAreaWidth()

```c
float OH_ArkUI_PointerEvent_GetTouchAreaWidth(const ArkUI_UIInputEvent* event, uint32_t pointerIndex)
```

**Description**


Obtains the width of the touch area for a pointer event. This API is applicable only to touch events generated by finger operations.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|
| uint32_t pointerIndex | Index of the target touch point in the multi-touch data list. The valid value range is [0, OH_ArkUI_PointerEvent_GetPointerCount(event) – 1]. If the value is out of range, the default value **0.0f** is returned. |

**Return value**

| Type| Description|
| -- | -- |
| float | Width of the touch area, in px.|

### OH_ArkUI_PointerEvent_GetTouchAreaHeight()

```c
float OH_ArkUI_PointerEvent_GetTouchAreaHeight(const ArkUI_UIInputEvent* event, uint32_t pointerIndex)
```

**Description**


Obtains the height of the touch area for a pointer event. This API is applicable only to touch events generated by finger operations.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|
| uint32_t pointerIndex | Index of the target touch point in the multi-touch data list. The valid value range is [0, OH_ArkUI_PointerEvent_GetPointerCount(event) – 1]. If the value is out of range, the default value **0.0f** is returned. |

**Return value**

| Type| Description|
| -- | -- |
| float | Height of the touch area, in px.|

### OH_ArkUI_PointerEvent_GetInteractionHand()

```c
int32_t OH_ArkUI_PointerEvent_GetInteractionHand(const ArkUI_UIInputEvent *event, ArkUI_InteractionHand *hand)
```

**Description**


Checks whether an event is triggered by a left-hand or right-hand tap. This API is valid only on products that support touch-based interaction hand identification. Use the device capability query API to check whether the current device supports this API. The value cannot be obtained in real time when the button is pressed. Before the system completes the result inference, **NONE** is returned by default. Therefore, do not use the return value in the pressing phase as the final identification result.

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md) *event | Pointer to the UI input event.|
| [ArkUI_InteractionHand](#arkui_interactionhand) *hand | Pointer to the output parameter, which is used to receive the hand interaction information of the touch point. The return value is **ARKUI_EVENT_HAND_LEFT**, **ARKUI_EVENT_HAND_RIGHT**, or **ARKUI_EVENT_HAND_NONE**. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs, for example, the event pointer, hand output parameter, or pointer index is invalid. Check and pass valid parameters. |

### OH_ArkUI_PointerEvent_GetInteractionHandByIndex()

```c
int32_t OH_ArkUI_PointerEvent_GetInteractionHandByIndex(const ArkUI_UIInputEvent *event, int32_t pointerIndex, ArkUI_InteractionHand *hand)
```

**Description**


Checks whether an event is triggered by a left-hand or right-hand tap. This API is valid only on products that support touch-based interaction hand identification. The value cannot be obtained in real time when the button is pressed. Before the system completes the result inference, **NONE** is returned by default. Therefore, do not use the return value in the pressing phase as the final identification result.

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md) *event | Pointer to the UI input event.|
| int32_t pointerIndex | Index of the target touch point in the multi-touch data list. The valid value range is [0, OH_ArkUI_PointerEvent_GetPointerCount(event) – 1]. Negative indexes are not supported. If the value is out of range, [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. |
| [ArkUI_InteractionHand](#arkui_interactionhand) *hand | Whether the touch point is from the left or right hand. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs, for example, the event pointer, hand output parameter, or pointer index is invalid. Check and pass valid parameters. |

### OH_ArkUI_PointerEvent_GetHistorySize()

```c
uint32_t OH_ArkUI_PointerEvent_GetHistorySize(const ArkUI_UIInputEvent* event)
```

**Description**


Obtains the number of historical events from a [pointer event](../../ui/arkts-interaction-capability-overview.md#pointer-event). Pointer events supported by this API contain only touch and mouse events. A historical event is the raw event that occurs between the current event and the previous event. This API is applicable only to the move phase (touch or mouse movement) of a pointer event. If this API is called in other states, the default value **0** is returned. Touch events are supported since API version 12, and mouse events are supported since API version 26.0.0.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|

**Return value**

| Type| Description|
| -- | -- |
| uint32_t | Number of historical events.|

### OH_ArkUI_PointerEvent_GetHistoryEventTime()

```c
int64_t OH_ArkUI_PointerEvent_GetHistoryEventTime(const ArkUI_UIInputEvent* event, uint32_t historyIndex)
```

**Description**


Obtains the occurrence time of a historical event from a pointer event. Pointer events supported by this API contain only touch and mouse events. Touch events are supported since API version 12, and mouse events are supported since API version 26.0.0.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|
| uint32_t historyIndex | Index in the historical event data list, which must be less than the value returned by [OH_ArkUI_PointerEvent_GetHistorySize](#oh_arkui_pointerevent_gethistorysize). |

**Return value**

| Type| Description|
| -- | -- |
| int64_t | Time when the UI input event occurs, in ns. Returns **0** if a parameter error occurs.|

### OH_ArkUI_PointerEvent_GetHistoryPointerCount()

```c
uint32_t OH_ArkUI_PointerEvent_GetHistoryPointerCount(const ArkUI_UIInputEvent* event, uint32_t historyIndex)
```

**Description**


Obtains the number of contact points in a specific historical event from a pointer event. Pointer events supported by this API contain only touch events.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|
| uint32_t historyIndex | Index in the historical event data list, which must be less than the value returned by [OH_ArkUI_PointerEvent_GetHistorySize](#oh_arkui_pointerevent_gethistorysize). |

**Return value**

| Type| Description|
| -- | -- |
| uint32_t | Number of contact points in the specified historical event.|

### OH_ArkUI_PointerEvent_GetHistoryPointerId()

```c
int32_t OH_ArkUI_PointerEvent_GetHistoryPointerId(const ArkUI_UIInputEvent* event, uint32_t pointerIndex, uint32_t historyIndex)
```

**Description**


Obtains the unique ID of a contact point in a specific historical event from a pointer event. Pointer events supported by this API contain only touch events. The ID distinguishes between multiple touch points from the same input device. The return value itself does not have any other meaning beyond identifying the touch point.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|
| uint32_t pointerIndex | Index in the multi-touch data list of a specific historical event. The valid value range is [0, OH_ArkUI_PointerEvent_GetHistoryPointerCount(event, historyIndex) – 1]. If the value is out of range, an abnormal parameter result is returned. |
| uint32_t historyIndex | Index in the historical event data list, which must be less than the value returned by [OH_ArkUI_PointerEvent_GetHistorySize](#oh_arkui_pointerevent_gethistorysize). |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | ID of the corresponding contact point in the specified historical event.|

### OH_ArkUI_PointerEvent_GetHistoryX()

```c
float OH_ArkUI_PointerEvent_GetHistoryX(const ArkUI_UIInputEvent* event, uint32_t pointerIndex, uint32_t historyIndex)
```

**Description**


Obtains the X-coordinate of a specific contact point in a specific historical event relative to the upper left corner of the current component from a pointer event. Pointer events supported by this API contain only touch and mouse events. For mouse events, this API returns the default value **0.0f** if the given value of **pointerIndex** is greater than **0**. Touch events are supported since API version 12, and mouse events are supported since API version 26.0.0.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|
| uint32_t pointerIndex | Index in the multi-touch data list. The valid value range is [0, OH_ArkUI_PointerEvent_GetHistoryPointerCount(event, historyIndex) – 1]. For mouse events, this API returns the default value **0.0f** if the value of this parameter is greater than 0. |
| uint32_t historyIndex | Index in the historical event data list, which must be less than the value returned by [OH_ArkUI_PointerEvent_GetHistorySize](#oh_arkui_pointerevent_gethistorysize). |

**Return value**

| Type| Description|
| -- | -- |
| float | X-coordinate of the specific contact point in the specific historical event relative to the upper left corner of the current component, in px. Returns **0.0f** if a parameter error occurs.|

### OH_ArkUI_PointerEvent_GetHistoryY()

```c
float OH_ArkUI_PointerEvent_GetHistoryY(const ArkUI_UIInputEvent* event, uint32_t pointerIndex, uint32_t historyIndex)
```

**Description**


Obtains the Y-coordinate of a specific contact point in a specific historical event relative to the upper left corner of the current component from a pointer event. Pointer events supported by this API contain only touch and mouse events. For mouse events, this API returns the default value **0.0f** if the given value of **pointerIndex** is greater than **0**. Touch events are supported since API version 12, and mouse events are supported since API version 26.0.0.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|
| uint32_t pointerIndex | Index in the multi-touch data list. The valid value range is [0, OH_ArkUI_PointerEvent_GetHistoryPointerCount(event, historyIndex) – 1]. For mouse events, this API returns the default value **0.0f** if the value of this parameter is greater than 0. |
| uint32_t historyIndex | Index in the historical event data list, which must be less than the value returned by [OH_ArkUI_PointerEvent_GetHistorySize](#oh_arkui_pointerevent_gethistorysize). |

**Return value**

| Type| Description|
| -- | -- |
| float | Y-coordinate of the specific contact point in the specific historical event relative to the upper left corner of the current component, in px. Returns **0.0f** if a parameter error occurs.|

### OH_ArkUI_PointerEvent_GetHistoryWindowX()

```c
float OH_ArkUI_PointerEvent_GetHistoryWindowX(const ArkUI_UIInputEvent* event, uint32_t pointerIndex, uint32_t historyIndex)
```

**Description**


Obtains the X-coordinate of a specific contact point in a specific historical event relative to the upper left corner of the current application window from a pointer event. Pointer events supported by this API contain only touch and mouse events. For mouse events, this API returns the default value **0.0f** if the given value of **pointerIndex** is greater than **0**. Touch events are supported since API version 12, and mouse events are supported since API version 26.0.0.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|
| uint32_t pointerIndex | Index in the multi-touch data list. The valid value range is [0, OH_ArkUI_PointerEvent_GetHistoryPointerCount(event, historyIndex) – 1]. For mouse events, this API returns the default value **0.0f** if the value of this parameter is greater than 0. |
| uint32_t historyIndex | Index in the historical event data list, which must be less than the value returned by [OH_ArkUI_PointerEvent_GetHistorySize](#oh_arkui_pointerevent_gethistorysize). |

**Return value**

| Type| Description|
| -- | -- |
| float | X-coordinate of the specific contact point in the specific historical event relative to the upper left corner of the current application window, in px. Returns **0.0f** if a parameter error occurs.|

### OH_ArkUI_PointerEvent_GetHistoryWindowY()

```c
float OH_ArkUI_PointerEvent_GetHistoryWindowY(const ArkUI_UIInputEvent* event, uint32_t pointerIndex, uint32_t historyIndex)
```

**Description**


Obtains the Y-coordinate of a specific contact point in a specific historical event relative to the upper left corner of the current application window from a pointer event. Pointer events supported by this API contain only touch and mouse events. For mouse events, this API returns the default value **0.0f** if the given value of **pointerIndex** is greater than **0**. Touch events are supported since API version 12, and mouse events are supported since API version 26.0.0.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|
| uint32_t pointerIndex | Index in the multi-touch data list. The valid value range is [0, OH_ArkUI_PointerEvent_GetHistoryPointerCount(event, historyIndex) – 1]. For mouse events, this API returns the default value **0.0f** if the value of this parameter is greater than 0. |
| uint32_t historyIndex | Index in the historical event data list, which must be less than the value returned by [OH_ArkUI_PointerEvent_GetHistorySize](#oh_arkui_pointerevent_gethistorysize). |

**Return value**

| Type| Description|
| -- | -- |
| float | Y-coordinate of the specific contact point in the specific historical event relative to the upper left corner of the current application window, in px. Returns **0.0f** if a parameter error occurs.|

### OH_ArkUI_PointerEvent_GetHistoryDisplayX()

```c
float OH_ArkUI_PointerEvent_GetHistoryDisplayX(const ArkUI_UIInputEvent* event, uint32_t pointerIndex, uint32_t historyIndex)
```

**Description**


Obtains the X-coordinate of a specific contact point in a specific historical event relative to the upper left corner of the current screen from a pointer event. Pointer events supported by this API contain only touch and mouse events. For mouse events, this API returns the default value **0.0f** if the given value of **pointerIndex** is greater than **0**. Touch events are supported since API version 12, and mouse events are supported since API version 26.0.0.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|
| uint32_t pointerIndex | Index in the multi-touch data list. The valid value range is [0, OH_ArkUI_PointerEvent_GetHistoryPointerCount(event, historyIndex) – 1]. For mouse events, this API returns the default value **0.0f** if the value of this parameter is greater than 0. |
| uint32_t historyIndex | Index in the historical event data list, which must be less than the value returned by [OH_ArkUI_PointerEvent_GetHistorySize](#oh_arkui_pointerevent_gethistorysize). |

**Return value**

| Type| Description|
| -- | -- |
| float | X-coordinate of the specific contact point in the specific historical event relative to the upper left corner of the current screen, in px. Returns **0.0f** if a parameter error occurs.|

### OH_ArkUI_PointerEvent_GetHistoryDisplayY()

```c
float OH_ArkUI_PointerEvent_GetHistoryDisplayY(const ArkUI_UIInputEvent* event, uint32_t pointerIndex, uint32_t historyIndex)
```

**Description**


Obtains the Y-coordinate of a specific contact point in a specific historical event relative to the upper left corner of the current screen from a pointer event. Pointer events supported by this API contain only touch and mouse events. For mouse events, this API returns the default value **0.0f** if the given value of **pointerIndex** is greater than **0**. Touch events are supported since API version 12, and mouse events are supported since API version 26.0.0.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|
| uint32_t pointerIndex | Index in the multi-touch data list. The valid value range is [0, OH_ArkUI_PointerEvent_GetHistoryPointerCount(event, historyIndex) – 1]. For mouse events, this API returns the default value **0.0f** if the value of this parameter is greater than 0. |
| uint32_t historyIndex | Index in the historical event data list, which must be less than the value returned by [OH_ArkUI_PointerEvent_GetHistorySize](#oh_arkui_pointerevent_gethistorysize). |

**Return value**

| Type| Description|
| -- | -- |
| float | Y-coordinate of the specific contact point in the specific historical event relative to the upper left corner of the current screen, in px. Returns **0.0f** if a parameter error occurs.|

### OH_ArkUI_PointerEvent_GetHistoryGlobalDisplayX()

```c
float OH_ArkUI_PointerEvent_GetHistoryGlobalDisplayX(const ArkUI_UIInputEvent* event, uint32_t pointerIndex, uint32_t historyIndex)
```

**Description**


Obtains the X-coordinate relative to the global display for a specific touch point in a historical event from a pointer event at the given pointer index and history index. Pointer events supported by this API contain only touch and mouse events. Position information can only be obtained from pointer events. For mouse events, if the provided **pointerIndex** is greater than 0, this API always returns the default value **0.0f**. Touch events are supported since API version 20, and mouse events are supported since API version 26.0.0.

**Since**: 20


**Parameters**

| Name| Description                                                                                                                  |
| -- |----------------------------------------------------------------------------------------------------------------------|
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.                                                                                                    |
| uint32_t pointerIndex | Index in the multi-touch data list. The valid value range is [0, OH_ArkUI_PointerEvent_GetHistoryPointerCount(event, historyIndex) – 1]. For mouse events, this API returns the default value **0.0f** if the value of this parameter is greater than 0. |
| uint32_t historyIndex | Historical value to be returned. The value must be less than the value returned by [OH_ArkUI_PointerEvent_GetHistorySize](#oh_arkui_pointerevent_gethistorysize). |

**Return value**

| Type| Description|
| -- | -- |
| float | X-coordinate of the specific contact point in the specific historical event relative to the global display, in px. Returns **0.0f** if any parameter error occurs.|

### OH_ArkUI_PointerEvent_GetHistoryGlobalDisplayY()

```c
float OH_ArkUI_PointerEvent_GetHistoryGlobalDisplayY(const ArkUI_UIInputEvent* event, uint32_t pointerIndex, uint32_t historyIndex)
```

**Description**


Obtains the Y-coordinate relative to the global display for a specific touch point in a historical event from a pointer event at the given pointer index and history index. Pointer events supported by this API contain only touch and mouse events. Position information can only be obtained from pointer events. For mouse events, if the provided **pointerIndex** is greater than 0, this API always returns the default value **0.0f**. Touch events are supported since API version 20, and mouse events are supported since API version 26.0.0.

**Since**: 20


**Parameters**

| Name| Description                                                                                                                  |
| -- |----------------------------------------------------------------------------------------------------------------------|
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.                                                                                                    |
| uint32_t pointerIndex | Index in the multi-touch data list. The valid value range is [0, OH_ArkUI_PointerEvent_GetHistoryPointerCount(event, historyIndex) – 1]. For mouse events, this API returns the default value **0.0f** if the value of this parameter is greater than 0.  |
| uint32_t historyIndex | Historical value to be returned. The value must be less than the value returned by [OH_ArkUI_PointerEvent_GetHistorySize](#oh_arkui_pointerevent_gethistorysize). |

**Return value**

| Type| Description|
| -- | -- |
| float | Y-coordinate of the specific contact point in the specific historical event relative to the global display, in px. Returns **0.0f** if any parameter error occurs.|

### OH_ArkUI_PointerEvent_GetHistoryPressure()

```c
float OH_ArkUI_PointerEvent_GetHistoryPressure(const ArkUI_UIInputEvent* event, uint32_t pointerIndex, uint32_t historyIndex)
```

**Description**


Obtains the pressure applied to the touchscreen in a specific historical event from a pointer event (such as a touch event). Pointer events supported by this API contain only touch events. The value of **historyIndex** must be less than the number of historical events returned by **OH_ArkUI_PointerEvent_GetHistorySize**.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|
| uint32_t pointerIndex | Index in the multi-touch data list of a specific historical event. The valid value range is [0, OH_ArkUI_PointerEvent_GetHistoryPointerCount(event, historyIndex) – 1]. For mouse events, this API returns the default value **0.0f** if the value of this parameter is greater than 0. |
| uint32_t historyIndex | Index in the historical event data list. The value must be less than the value returned by [OH_ArkUI_PointerEvent_GetHistorySize](capi-ui-input-event-h.md#oh_arkui_pointerevent_gethistorysize). |

**Return value**

| Type| Description|
| -- | -- |
| float | Touch pressure generated by the current pointer event. The value range is [0, 1]. The pressure is positively correlated with the value. If the parameter is abnormal, the default value **0.0f** is returned. On some devices, the return value may be greater than 1 due to different hardware parameter configurations.|

### OH_ArkUI_PointerEvent_GetHistoryTiltX()

```c
float OH_ArkUI_PointerEvent_GetHistoryTiltX(const ArkUI_UIInputEvent* event, uint32_t pointerIndex, uint32_t historyIndex)
```

**Description**


Obtains the angle relative to the YZ plane in a specific historical event from a pointer event (such as a touch event). The value range is [-90, 90], in deg. A positive value indicates a rightward tilt. This API is applicable only to stylus-based touch events from devices that support tilt reporting. The value of **historyIndex** must be less than the number of historical events returned by **OH_ArkUI_PointerEvent_GetHistorySize**.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|
| uint32_t pointerIndex | Index in the multi-touch data list of a specific historical event. The valid value range is [0, OH_ArkUI_PointerEvent_GetHistoryPointerCount(event, historyIndex) – 1]. If the value is out of range, an abnormal parameter result is returned. |
| uint32_t historyIndex | Index in the historical event data list. The value must be less than the value returned by [OH_ArkUI_PointerEvent_GetHistorySize](capi-ui-input-event-h.md#oh_arkui_pointerevent_gethistorysize). |

**Return value**

| Type| Description|
| -- | -- |
| float | Angle relative to the YZ plane.|

### OH_ArkUI_PointerEvent_GetHistoryTiltY()

```c
float OH_ArkUI_PointerEvent_GetHistoryTiltY(const ArkUI_UIInputEvent* event, uint32_t pointerIndex, uint32_t historyIndex)
```

**Description**


Obtains the angle relative to the XZ plane in a specific historical event from a pointer event (such as a touch event). The value range is [-90, 90], in deg. A positive value indicates a downward tilt. This API is applicable only to stylus-based touch events from devices that support tilt reporting. The value of **historyIndex** must be less than the number of historical events returned by **OH_ArkUI_PointerEvent_GetHistorySize**.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|
| uint32_t pointerIndex | Index in the multi-touch data list of a specific historical event. The valid value range is [0, OH_ArkUI_PointerEvent_GetHistoryPointerCount(event, historyIndex) – 1]. If the value is out of range, an abnormal parameter result is returned. |
| uint32_t historyIndex | Index in the historical event data list. The value must be less than the value returned by [OH_ArkUI_PointerEvent_GetHistorySize](capi-ui-input-event-h.md#oh_arkui_pointerevent_gethistorysize). |

**Return value**

| Type| Description|
| -- | -- |
| float | Angle relative to the XZ plane.|

### OH_ArkUI_PointerEvent_GetHistoryTouchAreaWidth()

```c
float OH_ArkUI_PointerEvent_GetHistoryTouchAreaWidth(const ArkUI_UIInputEvent* event, uint32_t pointerIndex, uint32_t historyIndex)
```

**Description**


Obtains the width of the touch area in a specific historical event from a pointer event (such as a touch event). This API is applicable only to touch events generated by finger operations, and the value of **historyIndex** must be less than the number of historical events returned by **OH_ArkUI_PointerEvent_GetHistorySize**.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|
| uint32_t pointerIndex | Index of the target touch point in the multi-touch data list.|
| uint32_t historyIndex | Index in the historical event data list. The value must be less than the value returned by [OH_ArkUI_PointerEvent_GetHistorySize](capi-ui-input-event-h.md#oh_arkui_pointerevent_gethistorysize). |

**Return value**

| Type| Description|
| -- | -- |
| float | Width of the touch area, in px.|

### OH_ArkUI_PointerEvent_GetHistoryTouchAreaHeight()

```c
float OH_ArkUI_PointerEvent_GetHistoryTouchAreaHeight(const ArkUI_UIInputEvent* event, uint32_t pointerIndex, uint32_t historyIndex)
```

**Description**


Obtains the height of the touch area in a specific historical event from a pointer event (such as a touch event). This API is applicable only to touch events generated by finger operations, and the value of **historyIndex** must be less than the number of historical events returned by **OH_ArkUI_PointerEvent_GetHistorySize**.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|
| uint32_t pointerIndex | Index in the multi-touch data list. The value must be less than the value returned by [OH_ArkUI_PointerEvent_GetHistorySize](capi-ui-input-event-h.md#oh_arkui_pointerevent_gethistorysize). |
| uint32_t historyIndex | Index in the historical event data list. The value must be less than the value returned by [OH_ArkUI_PointerEvent_GetHistorySize](capi-ui-input-event-h.md#oh_arkui_pointerevent_gethistorysize). |

**Return value**

| Type| Description|
| -- | -- |
| float | Height of the touch area, in px.|

### OH_ArkUI_AxisEvent_GetVerticalAxisValue()

```c
double OH_ArkUI_AxisEvent_GetVerticalAxisValue(const ArkUI_UIInputEvent* event)
```

**Description**

Obtains the value of the vertical scroll axis for this axis event. This value is typically generated by mouse wheel scrolling or two-finger vertical swiping on a touchpad.

If the value is triggered by mouse wheel scrolling:
1. The reported value is in degrees, representing the angle increment of a single scroll, not the total scroll amount.
2. The reported value includes the user's scroll step configuration ([OH_ArkUI_AxisEvent_GetScrollStep](#oh_arkui_axisevent_getscrollstep)).
3. The sign of the value indicates the direction: negative for forward scrolling and positive for backward scrolling.

If the value is generated by two-finger vertical swiping on a touchpad:
1. The reported value is in pixels, representing the scroll increment of a single scroll, not the total scroll amount.
2. The reported value is not affected by the user's scroll step configuration ([OH_ArkUI_AxisEvent_GetScrollStep](#oh_arkui_axisevent_getscrollstep)).
3. The sign of the value indicates the direction: When two fingers swipe from top to bottom, the reported value is negative. When two fingers swipe from bottom to top, the reported value is positive.
4. The direction is affected by the natural scrolling in the system settings.

Generally, the vertical scroll axis event can only drive the response to vertical swipe gestures. However, if the scrollable directions of the swipe gestures under the mouse pointer are consistent with the direction of the vertical scroll axis event, the vertical scroll axis event can drive these swipe gestures to respond, even if they are defined as horizontal.


**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|

**Return value**

| Type| Description|
| -- | -- |
| double | Value of the vertical scroll axis of the current axis event. Returns **0.0** if any parameter error occurs.|

### OH_ArkUI_AxisEvent_GetHorizontalAxisValue()

```c
double OH_ArkUI_AxisEvent_GetHorizontalAxisValue(const ArkUI_UIInputEvent* event)
```

**Description**


Obtains the value of the horizontal scroll axis for this axis event. This value is generated by two-finger horizontal swiping on a touchpad.

1. The reported value is in pixels, representing the scroll increment of a single scroll, not the total scroll amount.
2. The reported value is not affected by the user's scroll step configuration ([OH_ArkUI_AxisEvent_GetScrollStep](#oh_arkui_axisevent_getscrollstep)).
3. The sign of the value indicates the direction: When two fingers swipe from left to right, the reported value is negative. When two fingers swipe from right to left, the reported value is positive.
4. The direction is affected by the natural scrolling in the system settings.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|

**Return value**

| Type| Description|
| -- | -- |
| double | Value of the horizontal scroll axis of the current axis event. Returns **0.0** if any parameter error occurs.|

### OH_ArkUI_AxisEvent_GetPinchAxisScaleValue()

```c
double OH_ArkUI_AxisEvent_GetPinchAxisScaleValue(const ArkUI_UIInputEvent* event)
```

**Description**


Obtains the scale value of the pinch axis for this axis event. The value is generated by the pinch or zoom operation with two fingers on the touchpad. When the system identifies a pinch operation, the positions of the two fingers are used as the initial state, and the scale value is 1.0. During the pinch operation, the scale value decreases from 1.0 towards 0.0 when the user pinches inward and increases from 1.0 when the user spreads fingers outward.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|

**Return value**

| Type| Description|
| -- | -- |
| double | Scale value of the pinch axis of the current axis event. Returns **0.0** if any parameter error occurs.|

### OH_ArkUI_AxisEvent_GetAxisAction()

```c
int32_t OH_ArkUI_AxisEvent_GetAxisAction(const ArkUI_UIInputEvent* event)
```

**Description**


Obtains the action type of this axis event.

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Action type of the current axis event. For details, see [anonymous7](#anonymous7). If a non-axis event is input, **0** is returned by default.|

### OH_ArkUI_AxisEvent_HasAxis()

```c
int32_t OH_ArkUI_AxisEvent_HasAxis(const ArkUI_UIInputEvent* event, int32_t axis)
```

**Description**


Checks whether this axis event contains the specified axis type.

**Since**: 22


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|
| int32_t axis | Axis type of the axis event, specified using [UI_AXIS_TYPE](#anonymous8).|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Whether the current axis event contains the specified axis type. Returns **true** if the axis event contains the specified axis type, and **false** otherwise.|

### OH_ArkUI_PointerEvent_SetInterceptHitTestMode()

```c
int32_t OH_ArkUI_PointerEvent_SetInterceptHitTestMode(const ArkUI_UIInputEvent* event, HitTestMode mode)
```

**Description**


Sets the hit test mode to control whether the component itself, its child components, sibling components, and ancestor components participate in the touch hit test when a basic touch event is received. This API is used in scenarios where the touch event distribution scope needs to be adjusted. This API only applies to scenarios raw input events are received, such as when **NODE_ON_TOUCH** is used for touch event handling. It cannot be used with **ArkUI_UIInputEvent** objects obtained from gesture events through [OH_ArkUI_GestureEvent_GetRawInputEvent](capi-native-gesture-h.md#oh_arkui_gestureevent_getrawinputevent).

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|
| [HitTestMode](capi-ui-input-event-h.md#hittestmode) mode | Hit test mode. **HTM_DEFAULT** applies to the scenario where the node itself and its child nodes respond to the hit test, but block the hit test of sibling nodes. **HTM_BLOCK** applies to the scenario where only the node itself responds to the hit test and blocks the hit test of its child nodes, sibling nodes, and ancestor nodes. **HTM_TRANSPARENT** applies to the scenario where the node itself and its child nodes respond to the touch test but do not block the hit test of sibling nodes or ancestor nodes. **HTM_NONE** applies to the scenario where the node itself does not respond to the hit test and does not affect the hit test of other nodes. **HTM_BLOCK_HIERARCHY** applies to the scenario where the node itself and its child nodes respond to the hit test, but block the hit test of sibling nodes with lower priorities and the parent node. **HTM_BLOCK_DESCENDANTS** applies to the scenario where the node itself and its all descendants nodes do not respond to the hit test and do not affect the hit test of ancestor nodes. Select a mode based on the required node response range and blocking relationship. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | State code of the hit test mode setting result. If 0 is returned, the setting is successful. If a non-zero value is returned, the setting fails. |

### OH_ArkUI_MouseEvent_GetMouseButton()

```c
int32_t OH_ArkUI_MouseEvent_GetMouseButton(const ArkUI_UIInputEvent* event)
```

**Description**


Obtains the button type of a mouse event.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Mouse button type. The value is defined by the [anonymous5](#anonymous5) enumeration. If the API is called in a non-mouse event, the return value is **-1**.|

### OH_ArkUI_MouseEvent_GetMouseAction()

```c
int32_t OH_ArkUI_MouseEvent_GetMouseAction(const ArkUI_UIInputEvent* event)
```

**Description**


Obtains the action type of a mouse event.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Mouse action type. The value is defined by the [anonymous4](#anonymous4) enumeration. If the API is called in a non-mouse event, the return value is **-1**.|

### OH_ArkUI_PointerEvent_SetStopPropagation()

```c
int32_t OH_ArkUI_PointerEvent_SetStopPropagation(const ArkUI_UIInputEvent* event, bool stopPropagation)
```

**Description**


Sets whether to prevent event bubbling. This API is applicable when the current component has handled a basic touch event and does not want the event to be passed to its parent component or other ancestor components. This API only applies to scenarios raw input events are received, such as when **NODE_ON_TOUCH** is used for touch event handling, and does not apply to axis events. It cannot be used with **ArkUI_UIInputEvent** objects obtained from gesture events through [OH_ArkUI_GestureEvent_GetRawInputEvent](capi-native-gesture-h.md#oh_arkui_gestureevent_getrawinputevent).

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|
| bool stopPropagation | Whether to stop event propagation. The value **true** means to stop event propagation, and **false** means the opposite.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code. The value **0** means success, and the value **401** means failure, which may be caused by invalid parameters. For example, the **event** pointer may be null. In this case, check whether the **event** pointer is null and pass a valid UI input event pointer. |

### OH_ArkUI_UIInputEvent_GetDeviceId()

```c
int32_t OH_ArkUI_UIInputEvent_GetDeviceId(const ArkUI_UIInputEvent* event)
```

**Description**


Obtains the device ID of the current UI input event.

**Since**: 14


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Device ID of the current UI input event.|

### OH_ArkUI_UIInputEvent_GetPressedKeys()

```c
int32_t OH_ArkUI_UIInputEvent_GetPressedKeys(const ArkUI_UIInputEvent* event, int32_t* pressedKeyCodes, int32_t* length)
```

**Description**


Obtains all pressed keys. Currently, only key events are supported.

**Since**: 14


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| int32_t* pressedKeyCodes | Pointer to the output parameter, which points to the key code array allocated by the caller. It is used to receive the key values of all pressed keys. The array capacity is specified by the input parameter **length**, and the actual number of pressed keys is output through **length**. |
| int32_t* length | Dual-purpose parameter: As input, it indicates the length of the provided **pressedKeyCodes** array; as output, it indicates the number of pressed keys.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_BUFFER_SIZE_NOT_ENOUGH](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the memory is insufficient. Check and increase the capacity of the **pressedKeyCodes** buffer.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. The possible cause is that the event pointer, **pressedKeyCodes**, or **length** is invalid. Check the parameters and try again. |

### OH_ArkUI_FocusAxisEvent_GetAxisValue()

```c
double OH_ArkUI_FocusAxisEvent_GetAxisValue(const ArkUI_UIInputEvent* event, int32_t axis)
```

**Description**


Obtains the axis value of a focus axis event.

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| int32_t axis | Axis type of the focus axis event. To read the horizontal, vertical, or depth control value of the game handle control, select **UI_FOCUS_AXIS_EVENT_ABS_X**, **UI_FOCUS_AXIS_EVENT_ABS_Y**, or **UI_FOCUS_AXIS_EVENT_ABS_Z**, respectively. To read the rotation control value, select **UI_FOCUS_AXIS_EVENT_ABS_RZ**, **UI_FOCUS_AXIS_EVENT_ABS_RX**, or **UI_FOCUS_AXIS_EVENT_ABS_RY**. To read the throttle, brake, rudder, or steering wheel control value, select **UI_FOCUS_AXIS_EVENT_ABS_GAS**, **UI_FOCUS_AXIS_EVENT_ABS_BRAKE**, **UI_FOCUS_AXIS_EVENT_ABS_RUDDER**, or **UI_FOCUS_AXIS_EVENT_ABS_WHEEL**, respectively. To read the hat control value, select **UI_FOCUS_AXIS_EVENT_ABS_HAT0X**, **UI_FOCUS_AXIS_EVENT_ABS_HAT0Y**, **UI_FOCUS_AXIS_EVENT_ABS_HAT1X**, **UI_FOCUS_AXIS_EVENT_ABS_HAT1Y**, **UI_FOCUS_AXIS_EVENT_ABS_HAT2X**, **UI_FOCUS_AXIS_EVENT_ABS_HAT2Y**, **UI_FOCUS_AXIS_EVENT_ABS_HAT3X**, or **UI_FOCUS_AXIS_EVENT_ABS_HAT3Y**. Select an enumerated value based on the game handle control axis to be read. |

**Return value**

| Type| Description|
| -- | -- |
| double | Axis value of the focus axis event. Returns **0.0** if any parameter error occurs.|

### OH_ArkUI_FocusAxisEvent_SetStopPropagation()

```c
int32_t OH_ArkUI_FocusAxisEvent_SetStopPropagation(const ArkUI_UIInputEvent* event, bool stopPropagation)
```

**Description**


Sets whether to prevent focus axis event bubbling. This API is applicable when the component has handled a focus axis event and does not want the event to be passed to its parent component or other ancestor components.

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|
| bool stopPropagation | Whether to stop event propagation. The value **true** means to stop event propagation, and **false** means the opposite.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_UIInputEvent_GetModifierKeyStates()

```c
int32_t OH_ArkUI_UIInputEvent_GetModifierKeyStates(const ArkUI_UIInputEvent* event, uint64_t* keys)
```

**Description**


Obtains the modifier key states for a UI input event. This API passes the states of all modifier keys through **keys** when the current event occurs. The application can perform a bitwise operation on keys and the modifier key types defined in [ArkUI_ModifierKeyName](capi-ui-input-event-h.md#arkui_modifierkeyname) to obtain the modifier keys that are pressed.

**Since**: 17


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| uint64_t* keys | Pointer to the combination of pressed modifier keys. The application can use bitwise operations to determine which keys are pressed.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. The possible cause is that the event pointer or the output parameter is invalid. Check and pass a valid parameter. |

### OH_ArkUI_AxisEvent_SetPropagation()

```c
int32_t OH_ArkUI_AxisEvent_SetPropagation(const ArkUI_UIInputEvent* event, bool propagation)
```

**Description**


Sets whether to enable axis event bubbling. By default, axis events do not bubble and are only sent to the first component that can respond to axis events. You can enable axis event bubbling when an axis event is received to allow the event to be passed to the next ancestor component in the response chain that can handle axis events. This API cannot be used on axis events obtained from gesture events.

**Since**: 17


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the UI input event.|
| bool propagation | Whether to enable event propagation. The value **true** means to enable event propagation, and **false** means the opposite.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_AxisEvent_GetScrollStep()

```c
int32_t OH_ArkUI_AxisEvent_GetScrollStep(const ArkUI_UIInputEvent* event)
```

**Description**


Obtains the scroll step coefficient for a wheel-based axis event. This value indicates the user-defined scroll step.

**Since**: 17


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the **ArkUI_UIInputEvent** object.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Scroll step configuration of the mouse wheel axis event. For non-mouse events, the default value **0** is returned.|

### OH_ArkUI_UIInputEvent_GetEventTargetWidth()

```c
float OH_ArkUI_UIInputEvent_GetEventTargetWidth(const ArkUI_UIInputEvent* event)
```

**Description**


Obtains the width of the component hit by an event.

**Since**: 17


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the **ArkUI_UIInputEvent** object.|

**Return value**

| Type| Description|
| -- | -- |
| float | Width of the component hit by an event, in pixels. If any parameter error occurs, **0.0f** is returned.|

### OH_ArkUI_UIInputEvent_GetEventTargetHeight()

```c
float OH_ArkUI_UIInputEvent_GetEventTargetHeight(const ArkUI_UIInputEvent* event)
```

**Description**


Obtains the height of the component hit by an event.

**Since**: 17


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the **ArkUI_UIInputEvent** object.|

**Return value**

| Type| Description|
| -- | -- |
| float | Height of the component hit by an event, in pixels. If any parameter error occurs, **0.0f** is returned.|

### OH_ArkUI_UIInputEvent_GetEventTargetPositionX()

```c
float OH_ArkUI_UIInputEvent_GetEventTargetPositionX(const ArkUI_UIInputEvent* event)
```

**Description**


Obtains the x-coordinate of the component hit by an event.

**Since**: 17


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the **ArkUI_UIInputEvent** object.|

**Return value**

| Type| Description|
| -- | -- |
| float | X-coordinate of the component hit by an event, in pixels. If any parameter error occurs, **0.0f** is returned.|

### OH_ArkUI_UIInputEvent_GetEventTargetPositionY()

```c
float OH_ArkUI_UIInputEvent_GetEventTargetPositionY(const ArkUI_UIInputEvent* event)
```

**Description**


Obtains the y-coordinate of the component hit by an event.

**Since**: 17


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the **ArkUI_UIInputEvent** object.|

**Return value**

| Type| Description|
| -- | -- |
| float | Y-coordinate of the component hit by an event, in pixels. If any parameter error occurs, **0.0f** is returned.|

### OH_ArkUI_UIInputEvent_GetEventTargetGlobalPositionX()

```c
float OH_ArkUI_UIInputEvent_GetEventTargetGlobalPositionX(const ArkUI_UIInputEvent* event)
```

**Description**


Obtains the global x-coordinate of the component hit by an event.

**Since**: 17


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the **ArkUI_UIInputEvent** object.|

**Return value**

| Type| Description|
| -- | -- |
| float | Global x-coordinate of the component hit by an event, in pixels. If any parameter error occurs, **0.0f** is returned.|

### OH_ArkUI_UIInputEvent_GetEventTargetGlobalPositionY()

```c
float OH_ArkUI_UIInputEvent_GetEventTargetGlobalPositionY(const ArkUI_UIInputEvent* event)
```

**Description**


Obtains the global y-coordinate of the component hit by an event.

**Since**: 17


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the **ArkUI_UIInputEvent** object.|

**Return value**

| Type| Description|
| -- | -- |
| float | Global y-coordinate of the component hit by an event, in pixels. If any parameter error occurs, **0.0f** is returned.|

### OH_ArkUI_PointerEvent_GetPressedTimeByIndex()

```c
int64_t OH_ArkUI_PointerEvent_GetPressedTimeByIndex(const ArkUI_UIInputEvent* event, uint32_t pointerIndex)
```

**Description**


Obtains the press time of a specific touch point. This API is effective only for touch events.

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| uint32_t pointerIndex | Index of the target touch point in the multi-touch data list. The valid value range is [0, OH_ArkUI_PointerEvent_GetPointerCount(event) – 1]. If the value is out of range, **0** is returned. |

**Return value**

| Type| Description|
| -- | -- |
| int64_t | Press time of the specific touch point, in ns. Returns **0** if any parameter error occurs.|

### OH_ArkUI_MouseEvent_GetRawDeltaX()

```c
float OH_ArkUI_MouseEvent_GetRawDeltaX(const ArkUI_UIInputEvent* event)
```

**Description**


Obtains the movement delta of the mouse along the X axis in a two-dimensional plane. The value is the original movement data of the mouse hardware, which is expressed in the unit of the mouse movement distance in the physical world. The reported value is determined by the hardware, not the physical or logical pixels of the screen.

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|

**Return value**

| Type| Description|
| -- | -- |
| float | Movement delta of the mouse device along the X axis in the two-dimensional plane, which is expressed in the unit of the mouse movement distance in the physical world. If any parameter error occurs, **0.0f** is returned.<br>Note: In versions earlier than API version 26.0.0, the return value is not the original movement data of the mouse hardware. Instead, the original data is scaled down by a factor of *X*, where *X* is the system display size rate. Since API version 26.0.0, the return value is the original movement data of the mouse hardware. |

### OH_ArkUI_MouseEvent_GetRawDeltaY()

```c
float OH_ArkUI_MouseEvent_GetRawDeltaY(const ArkUI_UIInputEvent* event)
```

**Description**


Obtains the movement delta of the mouse along the Y axis in a two-dimensional plane. The value is the original movement data of the mouse hardware, which is expressed in the unit of the mouse movement distance in the physical world. The reported value is determined by the hardware, not the physical or logical pixels of the screen.

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|

**Return value**

| Type| Description|
| -- | -- |
| float | Movement delta of the mouse device along the Y axis in the two-dimensional plane, which is expressed in the unit of the mouse movement distance in the physical world. If any parameter error occurs, **0.0f** is returned.<br>**Note:** In versions earlier than API version 26.0.0, the return value is not the original movement data of the mouse hardware. Instead, the original data is scaled down by a factor of *Y*, where *Y* is the system display size rate. Since API version 26.0.0, the return value is the original movement data of the mouse hardware. |

### OH_ArkUI_MouseEvent_GetPressedButtons()

```c
int32_t OH_ArkUI_MouseEvent_GetPressedButtons(const ArkUI_UIInputEvent* event, int32_t* pressedButtons, int32_t* length)
```

**Description**


Obtains the pressed buttons from a mouse event.

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| int32_t* pressedButtons | Array of the pressed buttons. Create an integer array to store the button values. For button code definitions, see [anonymous5](#anonymous5).|
| int32_t* length | Pointer to the dual-purpose parameter: As input, it indicates the length of the provided **pressedButtons** array; as output, it indicates the number of pressed keys. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input buffer size is invalid.|

### OH_ArkUI_UIInputEvent_GetTargetDisplayId()

```c
int32_t OH_ArkUI_UIInputEvent_GetTargetDisplayId(const ArkUI_UIInputEvent* event)
```

**Description**


Obtains the ID of the screen where the UI input event occurs.

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Screen ID. Returns **0** if any parameter error occurs.|

### OH_ArkUI_HoverEvent_IsHovered()

```c
bool OH_ArkUI_HoverEvent_IsHovered(const ArkUI_UIInputEvent* event)
```

**Description**


Checks whether the cursor is hovering over this component.

**Since**: 17


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|

**Return value**

| Type| Description|
| -- | -- |
| bool | Returns **true** if the cursor is hovering over the current component.<br>        Returns **false** if the cursor is not hovering over the current component.|

### OH_ArkUI_PointerEvent_CreateClonedEvent()

```c
int32_t OH_ArkUI_PointerEvent_CreateClonedEvent(const ArkUI_UIInputEvent* event, ArkUI_UIInputEvent** clonedEvent)
```

**Description**


Creates a cloned event pointer based on an event pointer. This API is effective only for touch events. After the API is successfully called, call **OH_ArkUI_PointerEvent_DestroyClonedEvent()** to destroy the cloned event pointer after the cloned event is used, which prevents resource leakage.

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)** clonedEvent | Double pointer to the output parameter, which points the newly created cloned **ArkUI_UIInputEvent** object written by the API. After the pointer is used, call **OH_ArkUI_PointerEvent_DestroyClonedEvent** to release the resources. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.|

### OH_ArkUI_PointerEvent_DestroyClonedEvent()

```c
int32_t OH_ArkUI_PointerEvent_DestroyClonedEvent(const ArkUI_UIInputEvent* event)
```

**Description**


Destroys a cloned event pointer created by **OH_ArkUI_PointerEvent_CreateClonedEvent()**. After using a cloned event, call this API to release resources.

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.<br>         Returns [ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input event pointer is not a cloned event pointer.|

### OH_ArkUI_PointerEvent_SetClonedEventLocalPosition()

```c
int32_t OH_ArkUI_PointerEvent_SetClonedEventLocalPosition(const ArkUI_UIInputEvent* event, float x, float y)
```

**Description**


Sets the x-coordinate and y-coordinate of a cloned event relative to the upper left corner of the current component. This API should be used after a cloned event is created by calling **OH_ArkUI_PointerEvent_CreateClonedEvent()**. The **SetClonedEvent** APIs of the same series are applicable only to cloned events.

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| float x | X-coordinate relative to the upper left corner of the current component, in px.|
| float y | Y-coordinate relative to the upper left corner of the current component, in px.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.<br>         Returns [ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input event pointer is not a cloned event pointer.|

### OH_ArkUI_PointerEvent_SetClonedEventLocalPositionByIndex()

```c
int32_t OH_ArkUI_PointerEvent_SetClonedEventLocalPositionByIndex(const ArkUI_UIInputEvent* event, float x, float y, int32_t pointerIndex)
```

**Description**


Sets the x-coordinate and y-coordinate of a specific contact point of a cloned event relative to the upper left corner of the current component. This API can be used only for the **ArkUI_UIInputEvent** cloned event pointer created by [OH_ArkUI_PointerEvent_CreateClonedEvent](#oh_arkui_pointerevent_createclonedevent).

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| float x | X-coordinate relative to the upper left corner of the current component, in px.|
| float y | Y-coordinate relative to the upper left corner of the current component, in px.|
| int32_t pointerIndex | Index of the target touch point in the multi-touch data list. The valid value range is [0, OH_ArkUI_PointerEvent_GetPointerCount(event) – 1]. Negative indexes are not supported. If the value is out of range, [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.<br>         Returns [ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input event pointer is not a cloned event pointer.|

### OH_ArkUI_PointerEvent_SetClonedEventActionType()

```c
int32_t OH_ArkUI_PointerEvent_SetClonedEventActionType(const ArkUI_UIInputEvent* event, int32_t actionType)
```

**Description**


Sets the action type of a cloned event. This API can be used only for the **ArkUI_UIInputEvent** cloned event pointer created by [OH_ArkUI_PointerEvent_CreateClonedEvent](#oh_arkui_pointerevent_createclonedevent).

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| int32_t actionType | Action type of the **ArkUI_UIInputEvent** cloned event. For a touch event, select **UI_TOUCH_EVENT_ACTION_DOWN**, **UI_TOUCH_EVENT_ACTION_MOVE**, **UI_TOUCH_EVENT_ACTION_UP**, or **UI_TOUCH_EVENT_ACTION_CANCEL** based on the press, movement, lift, or cancellation scenario. For a mouse event, select **UI_MOUSE_EVENT_ACTION_PRESS**, **UI_MOUSE_EVENT_ACTION_RELEASE**, **UI_MOUSE_EVENT_ACTION_MOVE**, or **UI_MOUSE_EVENT_ACTION_CANCEL** based on the press, release, movement, or cancellation scenario. For an axis event, select **UI_AXIS_EVENT_ACTION_BEGIN**, **UI_AXIS_EVENT_ACTION_UPDATE**, **UI_AXIS_EVENT_ACTION_END**, or **UI_AXIS_EVENT_ACTION_CANCEL** based on the start, update, end, or cancellation scenario. Select a value based on the event type and action phase of the cloned event. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.<br>         Returns [ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input event pointer is not a cloned event pointer.|

### OH_ArkUI_PointerEvent_SetClonedEventChangedFingerId()

```c
int32_t OH_ArkUI_PointerEvent_SetClonedEventChangedFingerId(const ArkUI_UIInputEvent* event, int32_t fingerId)
```

**Description**


Sets the touch point ID of a cloned pointer event. This API can be used only for the **ArkUI_UIInputEvent** cloned event pointer created by [OH_ArkUI_PointerEvent_CreateClonedEvent](#oh_arkui_pointerevent_createclonedevent).

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| int32_t fingerId | ID of the touch point that triggers the event.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.<br>         Returns [ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input event pointer is not a cloned event pointer.|

### OH_ArkUI_PointerEvent_SetClonedEventFingerIdByIndex()

```c
int32_t OH_ArkUI_PointerEvent_SetClonedEventFingerIdByIndex(const ArkUI_UIInputEvent* event, int32_t fingerId, int32_t pointerIndex)
```

**Description**


Sets the touch point ID of a specific contact point of a cloned event. This API can be used only for the **ArkUI_UIInputEvent** cloned event pointer created by [OH_ArkUI_PointerEvent_CreateClonedEvent](#oh_arkui_pointerevent_createclonedevent).

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| int32_t fingerId | Touch point ID of the specific contact point.|
| int32_t pointerIndex | Index of the target touch point in the multi-touch data list. The valid value range is [0, OH_ArkUI_PointerEvent_GetPointerCount(event) – 1]. Negative indexes are not supported. If the value is out of range, [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.<br>         Returns [ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input event pointer is not a cloned event pointer.|

### OH_ArkUI_PointerEvent_PostClonedEvent()

```c
int32_t OH_ArkUI_PointerEvent_PostClonedEvent(ArkUI_NodeHandle node, const ArkUI_UIInputEvent* event)
```

**Description**


Posts a cloned event to a specific node. Before using this API, call **OH_ArkUI_PointerEvent_CreateClonedEvent()** to create a cloned event and call APIs such as **OH_ArkUI_PointerEvent_SetClonedEventLocalPosition()** to set event attributes as required. After the cloned event is used, call **OH_ArkUI_PointerEvent_DestroyClonedEvent()** to destroy it.

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Target node.|
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.<br>         Returns [ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input event pointer is not a cloned event pointer.<br>         Returns [ARKUI_ERROR_CODE_POST_CLONED_COMPONENT_STATUS_ABNORMAL](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the component status is abnormal.<br>         Returns [ARKUI_ERROR_CODE_POST_CLONED_NO_COMPONENT_HIT_TO_RESPOND_TO_THE_EVENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if no component is hit to respond to the event.|

### OH_ArkUI_PointerEvent_CreateClonedPointerEvent()

```c
ArkUI_ErrorCode OH_ArkUI_PointerEvent_CreateClonedPointerEvent(const ArkUI_UIInputEvent* event, ArkUI_UIInputEvent** clonedEvent)
```

**Description**


Creates a clone event for a specified event. This API applies to touch, mouse, and axis events. After the API is successfully called, you can use the **OH_ArkUI_ClonedEvent_SetXXX** series APIs to set the attributes of the clone event. After using the clone event, call **OH_ArkUI_PointerEvent_DestroyClonedPointerEvent()** to destroy the cloned event to avoid resource leakage.

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)** clonedEvent | Double-pointer to the output parameter, which is used to receive the created **ArkUI_UIInputEvent** cloned event pointer. After using the pointer, call **OH_ArkUI_PointerEvent_DestroyClonedPointerEvent()** to destroy the event. |

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.|

### OH_ArkUI_PointerEvent_CreatePointerEvent()

```c
ArkUI_ErrorCode OH_ArkUI_PointerEvent_CreatePointerEvent(ArkUI_UIInputEvent** event, ArkUI_UIInputEvent_Type type)
```

**Description**


Creates a new event (not clone the existing event). This API applies to touch, mouse, and axis events. After the API is successfully called, use the **OH_ArkUI_ClonedEvent_SetXXX** series APIs to set event attributes. After using the event, call **OH_ArkUI_PointerEvent_DestroyClonedPointerEvent()** to destroy the event to avoid resource leakage.

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)** event | Double pointer to the output parameter, which is used to receive the newly created **ArkUI_UIInputEvent** object. After using the object, call **OH_ArkUI_PointerEvent_DestroyClonedPointerEvent()** to destroy it. |
| [ArkUI_UIInputEvent_Type](#arkui_uiinputevent_type) type | Event type of **ArkUI_UIInputEvent**. Select **ARKUI_UIINPUTEVENT_TYPE_TOUCH** when creating a touch event, which is used to simulate or process touch input. Select **ARKUI_UIINPUTEVENT_TYPE_AXIS** when creating an axis event, which is used to simulate or process mouse scroll wheel, touchpad scrolling, or pinch input. Select **ARKUI_UIINPUTEVENT_TYPE_MOUSE** when creating a mouse event, which is used to simulate or process mouse button or movement input. Select a value based on the type of the input device event to be created. |

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.|

### OH_ArkUI_PointerEvent_DestroyClonedPointerEvent()

```c
ArkUI_ErrorCode OH_ArkUI_PointerEvent_DestroyClonedPointerEvent(const ArkUI_UIInputEvent* event)
```

**Description**


Destroys a cloned event pointer. This API applies to touch, mouse, and axis events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect, for example, **event** is invalid or **type** is not supported by the corresponding event type. In this case, check the event pointer and action type parameter.<br>         Returns [ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input event pointer is not a cloned event pointer.|

### OH_ArkUI_ClonedEvent_SetActionType()

```c
ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetActionType(const ArkUI_UIInputEvent* event, int32_t type)
```

**Description**


Sets an action type for a cloned event. This API applies to touch, mouse, and axis events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| int32_t type | Action type of the cloned event, including [UI_TOUCH_EVENT_ACTION](#anonymous1) for the touch event, [UI_MOUSE_EVENT_ACTION](#anonymous4) for the mouse event, and [UI_AXIS_EVENT_ACTION](#anonymous7) for the axis event. |

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.<br>         Returns [ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input event pointer is not a cloned event pointer.|

### OH_ArkUI_ClonedEvent_SetSourceType()

```c
ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetSourceType(const ArkUI_UIInputEvent* event, int32_t sourceType)
```

**Description**


Sets a source type for a cloned event. This API applies to touch, mouse, and axis events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| int32_t sourceType | Source type of the clone event. The value can be **0**, **1**, **2**, **4**, or **5**. The value **0** indicates unknown, **1** indicates the mouse, **2** indicates the touchscreen, **4** indicates the keyboard, and **5** indicates the handle control. |

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.<br>         Returns [ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input event pointer is not a cloned event pointer.|

### OH_ArkUI_ClonedEvent_SetToolType()

```c
ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetToolType(const ArkUI_UIInputEvent* event, int32_t toolType)
```

**Description**


Sets a tool type for a cloned event. This API applies to touch, mouse, and axis events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| int32_t toolType | Tool type of the cloned event. Select **UI_INPUT_EVENT_TOOL_TYPE_FINGER** for finger operations, **UI_INPUT_EVENT_TOOL_TYPE_PEN** for stylus pen operations, **UI_INPUT_EVENT_TOOL_TYPE_MOUSE** for mouse operations, **UI_INPUT_EVENT_TOOL_TYPE_TOUCHPAD** for touchpad operations, **UI_INPUT_EVENT_TOOL_TYPE_JOYSTICK** for joystick operations, and **UI_INPUT_EVENT_TOOL_TYPE_UNKNOWN** if the tool type cannot be determined. Select a value based on the operation tool that generates the event. |

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.<br>         Returns [ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input event pointer is not a cloned event pointer.|

### OH_ArkUI_ClonedEvent_SetPressure()

```c
ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetPressure(const ArkUI_UIInputEvent* event, float pressure)
```

**Description**


Sets the pressure applied to a touchscreen for a cloned event. This API applies to touch events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| float pressure | Pressure applied to the touchscreen. The value range is [0, 1], including **0** and **1**. Some devices may support values greater than 1. The actual value range depends on the device capability. If an unsupported value is passed, [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. |

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect, for example, **event** is invalid or **pressure** does not meet the requirements. Check the **event** pointer and **pressure** parameter.<br>         Returns [ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input event pointer is not a cloned event pointer.<br>         If the event type is not supported, a non-touch event may have been passed. Pass a touch event and try again.|

### OH_ArkUI_ClonedEvent_SetPressureByIndex()

```c
ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetPressureByIndex(const ArkUI_UIInputEvent* event, float pressure, int32_t pointerIndex)
```

**Description**


Sets the pressure applied to a touchscreen for a specific touch point in a cloned event. This API applies to touch events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| float pressure | Pressure applied to the touchscreen. The value range is [0, 1], including **0** and **1**. Some devices may support values greater than 1. The actual value range depends on the device capability. If an unsupported value is passed, [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. |
| int32_t pointerIndex | Index of the target touch point in the multi-touch data list.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.<br>         Returns [ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input event pointer is not a cloned event pointer.<br>         Returns [ARKUI_ERROR_INPUT_EVENT_TYPE_NOT_SUPPORTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the event type is not supported.|

### OH_ArkUI_ClonedEvent_SetEventTime()

```c
ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetEventTime(const ArkUI_UIInputEvent* event, int64_t timestamp)
```

**Description**


Sets the time when a cloned UI input event occurs. This API applies to touch, mouse, and axis events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| int64_t timestamp | Time when the cloned UI input event occurs, in ns.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.<br>         Returns [ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input event pointer is not a cloned event pointer.|

### OH_ArkUI_ClonedEvent_SetDeviceId()

```c
ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetDeviceId(const ArkUI_UIInputEvent* event, int32_t deviceId)
```

**Description**


Sets the ID of the device that triggers a cloned UI input event. This API applies to touch, mouse, and axis events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| int32_t deviceId | ID of the device that triggers the cloned UI input event, which can be obtained by calling [OH_ArkUI_UIInputEvent_GetDeviceId](#oh_arkui_uiinputevent_getdeviceid).|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.<br>         Returns [ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input event pointer is not a cloned event pointer.|

### OH_ArkUI_ClonedEvent_SetTargetDisplayId()

```c
ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetTargetDisplayId(const ArkUI_UIInputEvent* event, int32_t targetDisplayId)
```

**Description**


Sets the ID of the display where a cloned UI input event occurs. This API applies to touch, mouse, and axis events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| int32_t targetDisplayId | ID of the display where the cloned UI input event occurs, which can be obtained by calling [OH_ArkUI_UIInputEvent_GetTargetDisplayId](#oh_arkui_uiinputevent_gettargetdisplayid).|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.<br>         Returns [ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input event pointer is not a cloned event pointer.|

### OH_ArkUI_ClonedEvent_SetChangedFingerId()

```c
ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetChangedFingerId(const ArkUI_UIInputEvent* event, int32_t fingerId)
```

**Description**


Sets the touch point ID for a cloned pointer event. This API applies to touch events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| int32_t fingerId | ID of the touch point that triggers the event, which can be obtained by calling [OH_ArkUI_PointerEvent_GetPointerId](#oh_arkui_pointerevent_getpointerid).|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect, for example, **event** is invalid or **pointerIndex** is out of the valid range. Check the event pointer and touch point index.<br>         Returns [ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input event pointer is not a cloned event pointer.<br>         If the event type is not supported, a non-touch event may have been passed. Pass a touch event and try again.|

### OH_ArkUI_ClonedEvent_SetFingerIdByIndex()

```c
ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetFingerIdByIndex(const ArkUI_UIInputEvent* event, int32_t fingerId, int32_t pointerIndex)
```

**Description**


Sets the touch point ID of a specific contact point for a cloned event. This API applies to touch events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| int32_t fingerId | Finger ID of a specific touch point, which can be obtained by calling [OH_ArkUI_PointerEvent_GetPointerId](#oh_arkui_pointerevent_getpointerid). |
| int32_t pointerIndex | Index of the target touch point in the multi-touch data list.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.<br>         Returns [ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input event pointer is not a cloned event pointer.<br>         Returns [ARKUI_ERROR_INPUT_EVENT_TYPE_NOT_SUPPORTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the event type is not supported.|

### OH_ArkUI_ClonedEvent_SetChangedWindowPosition()

```c
ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetChangedWindowPosition(const ArkUI_UIInputEvent* event, float x, float y)
```

**Description**


Sets the X-coordinate and Y-coordinate of a cloned event relative to the upper left corner of the current window. This API applies to touch, mouse, and axis events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| float x | X-coordinate of the event relative to the upper left corner of the current window, in px.|
| float y | Y-coordinate of the event relative to the upper left corner of the current window, in px.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.<br>         Returns [ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input event pointer is not a cloned event pointer.|

### OH_ArkUI_ClonedEvent_SetWindowPositionByIndex()

```c
ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetWindowPositionByIndex(const ArkUI_UIInputEvent* event, float x, float y, int32_t pointerIndex)
```

**Description**


Sets the X-coordinate and Y-coordinate of a specific contact point of a cloned event relative to the upper left corner of the current window. This API applies to touch events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| float x | X-coordinate of the event relative to the upper left corner of the current window, in px.|
| float y | Y-coordinate of the event relative to the upper left corner of the current window, in px.|
| int32_t pointerIndex | Index of the target touch point in the multi-touch data list. The valid value range is [0, OH_ArkUI_PointerEvent_GetPointerCount(event) – 1]. Negative indexes are not supported. If the value is out of range, [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. |

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.<br>         Returns [ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input event pointer is not a cloned event pointer.<br>         Returns [ARKUI_ERROR_INPUT_EVENT_TYPE_NOT_SUPPORTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the event type is not supported.|

### OH_ArkUI_ClonedEvent_SetChangedScreenPosition()

```c
ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetChangedScreenPosition(const ArkUI_UIInputEvent* event, float x, float y)
```

**Description**


Sets the X-coordinate and Y-coordinate of a cloned event relative to the upper left corner of the current screen. This API applies to touch, mouse, and axis events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| float x | X-coordinate of the event relative to the upper left corner of the current screen, in px.|
| float y | Y-coordinate of the event relative to the upper left corner of the current screen, in px.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.<br>         Returns [ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input event pointer is not a cloned event pointer.|

### OH_ArkUI_ClonedEvent_SetScreenPositionByIndex()

```c
ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetScreenPositionByIndex(const ArkUI_UIInputEvent* event, float x, float y, int32_t pointerIndex)
```

**Description**


Sets the X-coordinate and Y-coordinate of a specific contact point of a cloned event relative to the upper left corner of the current screen. This API applies to touch events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| float x | X-coordinate of the event relative to the upper left corner of the current screen, in px.|
| float y | Y-coordinate of the event relative to the upper left corner of the current screen, in px.|
| int32_t pointerIndex | Index of the target touch point in the multi-touch data list.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect, for example, **event** is invalid, **pointerIndex** is out of the valid range, or the coordinate parameters do not meet the requirements. Check the event pointer, touch point index, and coordinate parameters.<br>         Returns [ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input event pointer is not a cloned event pointer.<br>         If the event type is not supported, a non-touch event may have been passed. Pass a touch event and try again.|

### OH_ArkUI_ClonedEvent_SetChangedGlobalDisplayPosition()

```c
ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetChangedGlobalDisplayPosition(const ArkUI_UIInputEvent* event, float x, float y)
```

**Description**


Sets the coordinates for a cloned event in the [global coordinate system](../../windowmanager/window-terminology.md#global-coordinate-system). This API applies to touch events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| float x | X-coordinate of the event relative to the global display, in px.|
| float y | Y-coordinate of the event relative to the global display, in px.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.<br>         Returns [ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input event pointer is not a cloned event pointer.|

### OH_ArkUI_ClonedEvent_SetGlobalDisplayPositionByIndex()

```c
ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetGlobalDisplayPositionByIndex(const ArkUI_UIInputEvent* event, float x, float y, int32_t pointerIndex)
```

**Description**


Sets the coordinates for a cloned event in the [global coordinate system](../../windowmanager/window-terminology.md#global-coordinate-system). This API applies to touch events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| float x | X-coordinate of the event relative to the global display, in px.|
| float y | Y-coordinate of the event relative to the global display, in px.|
| int32_t pointerIndex | Index of the target touch point in the multi-touch data list. The valid value range is [0, OH_ArkUI_PointerEvent_GetPointerCount(event) – 1]. Negative indexes are not supported. If the value is out of range, [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. |

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.<br>         Returns [ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input event pointer is not a cloned event pointer.<br>         Returns [ARKUI_ERROR_INPUT_EVENT_TYPE_NOT_SUPPORTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the event type is not supported.|

### OH_ArkUI_ClonedEvent_SetHandleId()

```c
ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetHandleId(const ArkUI_UIInputEvent* event, int32_t eventHandleId)
```

**Description**


Sets the unique handle of an event processing session. This handle must be used for any further operations on the event. For a given finger, only one event with this handle is in the active state at a time. This API applies to touch, mouse, and axis events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| int32_t eventHandleId | Unique handle of an event processing session.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.<br>         Returns [ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input event pointer is not a cloned event pointer.|

### OH_ArkUI_ClonedEvent_SetTiltAngle()

```c
ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetTiltAngle(const ArkUI_UIInputEvent* event, float tiltX, float tiltY)
```

**Description**


Sets the tilt angle of a cloned event relative to the YZ and XZ planes. The value range of both **tiltX** and **tiltY** is [-90, 90], including **-90** and **90**. A positive value of **tiltX** indicates a tilt to the right, and a positive value of **tiltY** indicates a tilt downward. This API applies to touch events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| float tiltX | Tilt angle of the cloned event relative to the YZ plane, in deg.|
| float tiltY | Tilt angle of the cloned event relative to the XZ plane, in deg.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.<br>         Returns [ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input event pointer is not a cloned event pointer.<br>         Returns [ARKUI_ERROR_INPUT_EVENT_TYPE_NOT_SUPPORTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the event type is not supported.|

### OH_ArkUI_ClonedEvent_SetRollAngle()

```c
ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetRollAngle(const ArkUI_UIInputEvent* event, float rollAngle)
```

**Description**


Sets the rotation angle of the stylus around the Z-axis in a cloned event. This API applies to touch events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| float rollAngle | Rotation angle of the stylus around the Z-axis in the cloned event, in deg.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.<br>         Returns [ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input event pointer is not a cloned event pointer.<br>         Returns [ARKUI_ERROR_INPUT_EVENT_TYPE_NOT_SUPPORTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the event type is not supported.|

### OH_ArkUI_ClonedEvent_SetPressedKeys()

```c
ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetPressedKeys(const ArkUI_UIInputEvent* event, int32_t* pressedKeyCodes, int32_t length)
```

**Description**


Sets all pressed keys in a cloned event. This API applies to key events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| int32_t* pressedKeyCodes | Pointer to the array of all pressed key values. The value is [ArkUI_KeyCode](capi-native-key-event-h.md#arkui_keycode). |
| int32_t length | Length of the array of the pressed keys.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.<br>         Returns [ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input event pointer is not a cloned event pointer.|

### OH_ArkUI_ClonedEvent_SetChangedTouchArea()

```c
ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetChangedTouchArea(const ArkUI_UIInputEvent* event, float width, float height)
```

**Description**


Sets the width and height of the finger contact area for a cloned event. This API applies to touch events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| float width | Width of the touch area of the cloned event, in px.|
| float height | Height of the touch area of the cloned event, in px.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.<br>         Returns [ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input event pointer is not a cloned event pointer.<br>         Returns [ARKUI_ERROR_INPUT_EVENT_TYPE_NOT_SUPPORTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the event type is not supported.|

### OH_ArkUI_ClonedEvent_SetTouchAreaByIndex()

```c
ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetTouchAreaByIndex(const ArkUI_UIInputEvent* event, float width, float height, int32_t pointerIndex)
```

**Description**


Sets the width and height of the finger contact area for a specific contact point of a cloned event. This API applies to touch events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| float width | Width of the touch area of the cloned event, in px.|
| float height | Height of the touch area of the cloned event, in px.|
| int32_t pointerIndex | Index of the target touch point in the multi-touch data list. The valid value range is [0, OH_ArkUI_PointerEvent_GetPointerCount(event) – 1]. Negative indexes are not supported. If the value is out of range, [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. |

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.<br>         Returns [ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input event pointer is not a cloned event pointer.<br>         Returns [ARKUI_ERROR_INPUT_EVENT_TYPE_NOT_SUPPORTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the event type is not supported.|

### OH_ArkUI_ClonedEvent_SetChangedInteractionHand()

```c
ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetChangedInteractionHand(const ArkUI_UIInputEvent* event, int32_t hand)
```

**Description**


Sets whether a cloned event is triggered by the left or right hand. This API applies to touch events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| int32_t hand | Interaction hand type of the touch point. Select **ARKUI_EVENT_HAND_LEFT** when the system identifies the touch as a left-hand touch, **ARKUI_EVENT_HAND_RIGHT** when the system identifies the touch as a right-hand touch, and **ARKUI_EVENT_HAND_NONE** when the system cannot determine the hand. Set this parameter only when you need to simulate or correct the left-hand or right-hand attribute of the cloned touch event. |

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.<br>         Returns [ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input event pointer is not a cloned event pointer.<br>         Returns [ARKUI_ERROR_INPUT_EVENT_TYPE_NOT_SUPPORTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the event type is not supported.|

### OH_ArkUI_ClonedEvent_SetInteractionHandByIndex()

```c
ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetInteractionHandByIndex(const ArkUI_UIInputEvent* event, int32_t hand, int32_t pointerIndex)
```

**Description**


Sets whether a specific contact point of a cloned event is triggered by the left or right hand. This API applies to touch events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| int32_t hand | Whether the touch point is on the left or right hand. [ARKUI_EVENT_HAND_LEFT](#arkui_interactionhand) indicates the left hand, and [ARKUI_EVENT_HAND_RIGHT](#arkui_interactionhand) indicates the right hand.|
| int32_t pointerIndex | Index of the target touch point in the multi-touch data list. The valid value range is [0, OH_ArkUI_PointerEvent_GetPointerCount(event) – 1]. Negative indexes are not supported. If the value is out of range, [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. |

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.<br>         Returns [ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input event pointer is not a cloned event pointer.<br>         Returns [ARKUI_ERROR_INPUT_EVENT_TYPE_NOT_SUPPORTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the event type is not supported.|

### OH_ArkUI_ClonedEvent_SetPressedTimeByIndex()

```c
ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetPressedTimeByIndex(const ArkUI_UIInputEvent* event, int64_t pressedTime, int32_t pointerIndex)
```

**Description**


Sets the time when a specific touch point is pressed in a cloned event. This API applies to touch events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| int64_t pressedTime | Time when the specific touch point, in ns.|
| int32_t pointerIndex | Index of the target touch point in the multi-touch data list. The valid value range is [0, OH_ArkUI_PointerEvent_GetPointerCount(event) – 1]. Negative indexes are not supported. If the value is out of range, [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) is returned. |

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.<br>         Returns [ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input event pointer is not a cloned event pointer.<br>         Returns [ARKUI_ERROR_INPUT_EVENT_TYPE_NOT_SUPPORTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the event type is not supported.|

### OH_ArkUI_ClonedEvent_SetPinchAxisScaleValue()

```c
ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetPinchAxisScaleValue(const ArkUI_UIInputEvent* event, double pinchAxisScaleValue)
```

**Description**


Sets the pinch axis scaling value for a cloned event. This API applies to axis events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| double pinchAxisScaleValue | Pinch axis scaling value of the cloned axis event to control the pinch scaling state corresponding to the event. The value range is [0, +∞). |

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.<br>         Returns [ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input event pointer is not a cloned event pointer.<br>         Returns [ARKUI_ERROR_INPUT_EVENT_TYPE_NOT_SUPPORTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the event type is not supported.|

### OH_ArkUI_ClonedEvent_SetHorizontalAxisScaleValue()

```c
ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetHorizontalAxisScaleValue(const ArkUI_UIInputEvent* event, double horizontalAxisScaleValue)
```

**Description**


Sets the scaling value of the horizontal scroll axis for a cloned event. This API applies to axis events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| double horizontalAxisScaleValue | Horizontal axis scaling value, in px. This parameter is used to control the horizontal scrolling behavior of the event. |

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.<br>         Returns [ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input event pointer is not a cloned event pointer.<br>         Returns [ARKUI_ERROR_INPUT_EVENT_TYPE_NOT_SUPPORTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the event type is not supported.|

### OH_ArkUI_ClonedEvent_SetVerticalAxisScaleValue()

```c
ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetVerticalAxisScaleValue(const ArkUI_UIInputEvent* event, double verticalAxisScaleValue)
```

**Description**


Sets the scaling value of the vertical scroll axis for a cloned event. This API applies to axis events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| double verticalAxisScaleValue | Vertical axis scaling value, in px. This parameter is used to control the vertical scrolling behavior of the event. The unit is determined based on the event source. For a touchpad two-finger swipe event, the unit is px. For a mouse scroll wheel event, the unit is degree. |

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.<br>         Returns [ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input event pointer is not a cloned event pointer.<br>         Returns [ARKUI_ERROR_INPUT_EVENT_TYPE_NOT_SUPPORTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the event type is not supported.|

### OH_ArkUI_ClonedEvent_SetScrollStep()

```c
ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetScrollStep(const ArkUI_UIInputEvent* event, int32_t scrollStep)
```

**Description**


Sets the scrolling step coefficient for a cloned event. This API applies to axis events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| int32_t scrollStep | Scrolling step coefficient of the cloned event, which is used to control the scroll zoom effect of the mouse scroll wheel axis event. The value is an integer within the range of [0, 65535]. |

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>        Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.<br>         Returns [ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input event pointer is not a cloned event pointer.<br>         Returns [ARKUI_ERROR_INPUT_EVENT_TYPE_NOT_SUPPORTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the event type is not supported.|

### OH_ArkUI_ClonedEvent_SetMouseButton()

```c
ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetMouseButton(const ArkUI_UIInputEvent* event, int32_t button)
```

**Description**


Sets a button type for a cloned event. This API applies to mouse events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| int32_t button | Mouse button type of the cloned event. Select **UI_MOUSE_EVENT_BUTTON_LEFT** to simulate the left button, **UI_MOUSE_EVENT_BUTTON_RIGHT** to simulate the right button, **UI_MOUSE_EVENT_BUTTON_MIDDLE** to simulate the middle button, **UI_MOUSE_EVENT_BUTTON_BACK** to simulate the back button, **UI_MOUSE_EVENT_BUTTON_FORWARD** to simulate the forward button, or **UI_MOUSE_EVENT_BUTTON_NONE** when no mouse button is pressed. Select a value based on the mouse operation to be simulated. |

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.<br>         Returns [ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input event pointer is not a cloned event pointer.<br>         Returns [ARKUI_ERROR_INPUT_EVENT_TYPE_NOT_SUPPORTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the event type is not supported.|

### OH_ArkUI_ClonedEvent_SetRawDeltaX()

```c
ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetRawDeltaX(const ArkUI_UIInputEvent* event, float rawDeltaX)
```

**Description**


Sets the movement delta of the mouse along the x-axis in a two-dimensional plane. The value is the original movement data of the mouse hardware, which is expressed in the unit of the mouse movement distance in the physical world. This API applies to mouse events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| float rawDeltaX | X-axis offset of the mouse position relative to the position in the previously reported mouse event. The unit is the distance unit reported by the mouse hardware. |

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.<br>         Returns [ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input event pointer is not a cloned event pointer.<br>         Returns [ARKUI_ERROR_INPUT_EVENT_TYPE_NOT_SUPPORTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the event type is not supported.|

### OH_ArkUI_ClonedEvent_SetRawDeltaY()

```c
ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetRawDeltaY(const ArkUI_UIInputEvent* event, float rawDeltaY)
```

**Description**


Sets the movement delta of the mouse along the y-axis in a two-dimensional plane. The value is the original movement data of the mouse hardware, which is expressed in the unit of the mouse movement distance in the physical world. This API applies to mouse events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| float rawDeltaY | Y-axis offset of the mouse position relative to the position in the previously reported mouse event. The unit is the distance unit reported by the mouse hardware. |

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.<br>         Returns [ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input event pointer is not a cloned event pointer.<br>         Returns [ARKUI_ERROR_INPUT_EVENT_TYPE_NOT_SUPPORTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the event type is not supported.|

### OH_ArkUI_ClonedEvent_SetPressedButtons()

```c
ArkUI_ErrorCode OH_ArkUI_ClonedEvent_SetPressedButtons(const ArkUI_UIInputEvent* event, const int32_t* pressedButtons, int32_t length)
```

**Description**


Sets the pressed keys in a cloned event. This API applies to mouse events. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| const int32_t* pressedButtons | Pointer to the array of the pressed keys. For the values of the keys, see [anonymous5](#anonymous5).|
| int32_t length | Length of the array of the pressed keys.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.<br>         Returns [ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input event pointer is not a cloned event pointer.<br>         Returns [ARKUI_ERROR_INPUT_EVENT_TYPE_NOT_SUPPORTED](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the event type is not supported.|

### OH_ArkUI_PointerEvent_PostClonedEventWithStrategy()

```c
ArkUI_ErrorCode OH_ArkUI_PointerEvent_PostClonedEventWithStrategy(ArkUI_NodeHandle node, const ArkUI_UIInputEvent* event, ArkUI_CompetitionStrategy strategy)
```

**Description**


Posts a cloned event to a specific node using a specified competition policy. This API is applicable to the scenario where a cloned event is injected to a target node and whether the injected event competes with the existing gestures on the target node needs to be controlled. This API can be used only for the **ArkUI_UIInputEvent** objects created by [OH_ArkUI_PointerEvent_CreateClonedPointerEvent](#oh_arkui_pointerevent_createclonedpointerevent) and [OH_ArkUI_PointerEvent_CreatePointerEvent](#oh_arkui_pointerevent_createpointerevent).

**Since**: 24


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Target node.|
| [const ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|
| [ArkUI_CompetitionStrategy](#arkui_competitionstrategy) strategy | Competition strategy Select **ARKUI_COMPETITION_STRATEGY_DEFAULT** if the injected event needs to be processed independently and concurrently with the existing gestures on the target node. Select **ARKUI_COMPETITION_STRATEGY_COMPETITION** if the gestures of the injecting and injected parties need to compete with each other and only one party is processed. Select the corresponding policy based on whether gesture competition is required. |

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if an input parameter is incorrect, for example, the **node**, **event**, or **strategy** parameter is invalid. Check and pass a valid node, event pointer, and policy.<br>         Returns [ARKUI_ERROR_CODE_NOT_CLONED_POINTER_EVENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input event pointer is not a cloned event pointer.<br>         Returns [ARKUI_ERROR_CODE_POST_CLONED_COMPONENT_STATUS_ABNORMAL](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the component status is abnormal.<br>         Returns [ARKUI_ERROR_CODE_POST_CLONED_NO_COMPONENT_HIT_TO_RESPOND_TO_THE_EVENT](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if no component is hit to respond to the event.|

### OH_ArkUI_UIInputEvent_GetLatestStatus()

```c
ArkUI_ErrorCode OH_ArkUI_UIInputEvent_GetLatestStatus()
```

**Description**


Obtains the result code of the most recent API call related to an **ArkUI_UIInputEvent** object. This API is used only when you need to check whether an exception occurs after an API call related to the **ArkUI_UIInputEvent** object.

**Since**: 20

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code of the most recent API call related to the **ArkUI_UIInputEvent** object.|

### OH_ArkUI_UIInputEvent_GetCoastingAxisEvent()

```c
ArkUI_CoastingAxisEvent* OH_ArkUI_UIInputEvent_GetCoastingAxisEvent(ArkUI_UIInputEvent* event)
```
**Description**

Obtains the coasting axis event after obtaining the [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md) object from the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object. A valid event is available only when the user slides two fingers a certain distance on the touchpad and quickly releases them, and a component registered with the [NODE_ON_COASTING_AXIS_EVENT](capi-native-node-h.md#arkui_nodeeventtype) event exists at the pointer position.

The coasting axis event is triggered only when the user performs a two-finger swipe and releases on the touchpad, so it is exclusive to touchpad devices. This event generates axis values that gradually attenuate based on the initial swipe velocity after finger release. Due to factors such as refresh rate and performance constraints, the axis value of the current event may be higher or lower than the previous one. The following behavior will interrupt the coasting axis event and immediately trigger [ARKUI_COASTING_AXIS_EVENT_PHASE_END](#arkui_coastingaxiseventphase):
1. Touching the touchpad
2. Scrolling the mouse wheel
3. Clicking a node registered for coasting axis events Note that clicking nodes that are not registered with this event does not interrupt the current coasting axis event. For example, if node A registers the event and node B is being scrolled during coasting, clicking node B will not interrupt the event. Click event interruption is affected by [OH_ArkUI_PointerEvent_SetInterceptHitTestMode](#oh_arkui_pointerevent_setintercepthittestmode). If the tapped area contains any nodes that can respond to coasting axis events, the coasting axis event will be forcibly terminated.

4. Application hibernation (such as minimization and screen lock)

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)* event | Pointer to the target **ArkUI_UIInputEvent** object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_CoastingAxisEvent](capi-arkui-nativemodule-arkui-coastingaxisevent.md)* | Pointer to the coasting axis event. Returns a null pointer if no coasting axis event occurs or if parameters are invalid.|

### OH_ArkUI_CoastingAxisEvent_GetEventTime()

```c
int64_t OH_ArkUI_CoastingAxisEvent_GetEventTime(ArkUI_CoastingAxisEvent* event)
```
**Description**

Obtains the time when a coasting axis event occurs.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CoastingAxisEvent](capi-arkui-nativemodule-arkui-coastingaxisevent.md)* event | Pointer to the coasting axis event.|

**Return value**

| Type| Description|
| -- | -- |
| int64_t | Time when the coasting axis event occurs, in ns. If any parameter error occurs, **0** is returned.|

### OH_ArkUI_CoastingAxisEvent_GetPhase()

```c
ArkUI_CoastingAxisEventPhase OH_ArkUI_CoastingAxisEvent_GetPhase(ArkUI_CoastingAxisEvent* event)
```
**Description**

Obtains the scroll phase of the specified coasting axis event. When **[ARKUI_COASTING_AXIS_EVENT_PHASE_END](#arkui_coastingaxiseventphase)** is returned, the coasting effect should be stopped immediately.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CoastingAxisEvent](capi-arkui-nativemodule-arkui-coastingaxisevent.md)* event | Pointer to the coasting axis event.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_CoastingAxisEventPhase](#arkui_coastingaxiseventphase) | Event phase. For details, see [ArkUI_CoastingAxisEventPhase](#arkui_coastingaxiseventphase).<br>    Returns **ARKUI_COASTING_AXIS_EVENT_PHASE_NONE** if any parameter error occurs.|

### OH_ArkUI_CoastingAxisEvent_GetDeltaY()

```c
float OH_ArkUI_CoastingAxisEvent_GetDeltaY(ArkUI_CoastingAxisEvent* event)
```
**Description**

Obtains the vertical delta value of the specified coasting axis event. Unit: px, representing the single scroll increment (not the total scroll amount). Negative values indicate a downward direction (fingers swiping from top to bottom), and positive values indicate an upward direction (fingers swiping from bottom to top).

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CoastingAxisEvent](capi-arkui-nativemodule-arkui-coastingaxisevent.md)* event | Pointer to the coasting axis event.|

**Return value**

| Type| Description|
| -- | -- |
| float | Y-axis delta value, in px. Returns **0.0f** if any parameter error occurs.|

### OH_ArkUI_CoastingAxisEvent_GetDeltaX()

```c
float OH_ArkUI_CoastingAxisEvent_GetDeltaX(ArkUI_CoastingAxisEvent* event)
```
**Description**

Obtains the horizontal delta value of the specified coasting axis event. Unit: px, representing the single scroll increment (not the total scroll amount). Positive values indicate a rightward direction (fingers swiping from right to left), and negative values indicate a leftward direction (fingers swiping from left to right).

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CoastingAxisEvent](capi-arkui-nativemodule-arkui-coastingaxisevent.md)* event | Pointer to the coasting axis event.|

**Return value**

| Type| Description|
| -- | -- |
| float | X-axis delta value, in px. Returns **0.0f** if any parameter error occurs.|

### OH_ArkUI_CoastingAxisEvent_SetPropagation()

```c
int32_t OH_ArkUI_CoastingAxisEvent_SetPropagation(ArkUI_CoastingAxisEvent* event, bool propagation)
```
**Description**

Sets whether to enable bubbling for coasting axis events. By default, bubbling is disabled. This API is applicable when the current component has handled a coasting axis event and needs to pass the event to its ancestor components for collaborative scrolling effect processing.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CoastingAxisEvent](capi-arkui-nativemodule-arkui-coastingaxisevent.md)* event | Pointer to the coasting axis event.|
| bool propagation | Whether to enable event propagation. **true**: enable; **false**: disable.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.<br>        |

### OH_ArkUI_TouchTestInfo_GetTouchTestInfoList()

```c
ArkUI_ErrorCode OH_ArkUI_TouchTestInfo_GetTouchTestInfoList(ArkUI_TouchTestInfo* info,
    ArkUI_TouchTestInfoItemArray* array, int32_t* size);
```
**Description**

Obtains the array of touch test information items from the touch test information.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TouchTestInfo](./capi-arkui-nativemodule-arkui-touchtestinfo.md)* info | Pointer to the touch test information.|
| [ArkUI_TouchTestInfoItemArray](./capi-arkui-nativemodule-arkui-touchtestinfoitemhandlearray.md)* array | Pointer to the output parameter, which is used to receive the array of touch test information items. The elements in the array are touch test information items. The array size is returned through the **size** parameter. |
| int32_t* size | Pointer to the output parameter, which indicates the number of touch test information items returned in the array. |

**Return value**

| Type| Description|
| -- | -- |
| ArkUI_ErrorCode | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.<br>        |

### OH_ArkUI_TouchTestInfoItem_GetX()

```c
float OH_ArkUI_TouchTestInfoItem_GetX(const ArkUI_TouchTestInfoItem* info);
```
**Description**

Obtains the X coordinate relative to the upper left corner of the child component from the touch test information item, in px.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_TouchTestInfoItem](./capi-arkui-nativemodule-arkui-touchtestinfoitem.md)* info | Pointer to a touch test information item.|

**Return value**

| Type| Description|
| -- | -- |
| float | X coordinate relative to the upper left corner of the child component, in px. If the parameter value is incorrect, **0.0f** is returned.|

### OH_ArkUI_TouchTestInfoItem_GetY()

```c
float OH_ArkUI_TouchTestInfoItem_GetY(const ArkUI_TouchTestInfoItem* info);
```
**Description**

Obtains the Y coordinate relative to the upper left corner of the child component from the touch test information item, in px.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_TouchTestInfoItem](./capi-arkui-nativemodule-arkui-touchtestinfoitem.md)* info | Pointer to a touch test information item.|

**Return value**

| Type| Description|
| -- | -- |
| float | Y coordinate relative to the upper left corner of the child component, in px. If the parameter value is incorrect, **0.0f** is returned.|

### OH_ArkUI_TouchTestInfoItem_GetWindowX()

```c
float OH_ArkUI_TouchTestInfoItem_GetWindowX(const ArkUI_TouchTestInfoItem* info);
```
**Description**

Obtains the X coordinate relative to the upper left corner of the current application window from the touch test information item, in px.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_TouchTestInfoItem](./capi-arkui-nativemodule-arkui-touchtestinfoitem.md)* info | Pointer to a touch test information item.|

**Return value**

| Type| Description|
| -- | -- |
| float | X coordinate relative to the upper left corner of the current application window, in px. If the parameter value is incorrect, **0.0f** is returned.|

### OH_ArkUI_TouchTestInfoItem_GetWindowY()

```c
float OH_ArkUI_TouchTestInfoItem_GetWindowY(const ArkUI_TouchTestInfoItem* info);
```
**Description**

Obtains the Y coordinate relative to the upper left corner of the current application window from the touch test information item, in px.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_TouchTestInfoItem](./capi-arkui-nativemodule-arkui-touchtestinfoitem.md)* info | Pointer to a touch test information item.|

**Return value**

| Type| Description|
| -- | -- |
| float | Y coordinate relative to the upper left corner of the current application window, in px. If the parameter value is incorrect, **0.0f** is returned.|


### OH_ArkUI_TouchTestInfoItem_GetXRelativeToParent()

```c
float OH_ArkUI_TouchTestInfoItem_GetXRelativeToParent(const ArkUI_TouchTestInfoItem* info);
```
**Description**

Obtains the X coordinate relative to the upper left corner of the parent component from the touch test information item, in px.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_TouchTestInfoItem](./capi-arkui-nativemodule-arkui-touchtestinfoitem.md)* info | Pointer to a touch test information item.|

**Return value**

| Type| Description|
| -- | -- |
| float | X coordinate relative to the upper left corner of the parent component, in px. If the parameter value is incorrect, **0.0f** is returned.|

### OH_ArkUI_TouchTestInfoItem_GetYRelativeToParent()

```c
float OH_ArkUI_TouchTestInfoItem_GetYRelativeToParent(const ArkUI_TouchTestInfoItem* info);
```
**Description**

Obtains the Y coordinate relative to the upper left corner of the parent component from the touch test information item, in px.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_TouchTestInfoItem](./capi-arkui-nativemodule-arkui-touchtestinfoitem.md)* info | Pointer to a touch test information item.|

**Return value**

| Type| Description|
| -- | -- |
| float | Y coordinate relative to the upper left corner of the parent component, in px. If the parameter value is incorrect, **0.0f** is returned.|

### OH_ArkUI_TouchTestInfoItem_GetChildRect()

```c
ArkUI_ErrorCode OH_ArkUI_TouchTestInfoItem_GetChildRect(const ArkUI_TouchTestInfoItem* info, ArkUI_Rect* childRect);
```
**Description**

Obtains the boundary rectangle information of the child component from the touch test information item.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_TouchTestInfoItem](./capi-arkui-nativemodule-arkui-touchtestinfoitem.md)* info | Pointer to a touch test information item.|
| [ArkUI_Rect](./capi-arkui-nativemodule-arkui-rect.md)* childRect | Pointer to the boundary rectangle of the child component, which is used to store the obtained boundary rectangle information.|

**Return value**

| Type| Description|
| -- | -- |
| ArkUI_ErrorCode | Result code.<br>Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.<br>     |

### OH_ArkUI_TouchTestInfoItem_GetChildId()

```c
ArkUI_ErrorCode OH_ArkUI_TouchTestInfoItem_GetChildId(const ArkUI_TouchTestInfoItem* info, char* buffer,
    int32_t bufferSize);
```
**Description**

Obtains the ID of the child component from the touch test information item.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_TouchTestInfoItem](./capi-arkui-nativemodule-arkui-touchtestinfoitem.md)* info | Pointer to a touch test information item.|
| char* buffer | Pointer to the buffer provided by the caller, which is used to receive the obtained child component ID string. |
| int32_t bufferSize | Buffer size.|


**Return value**

| Type| Description|
| -- | -- |
| ArkUI_ErrorCode | Result code.<br>Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.<br>Returns [ARKUI_ERROR_CODE_BUFFER_SIZE_NOT_ENOUGH](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the buffer space is insufficient.|

### OH_ArkUI_TouchTestInfo_SetTouchResultStrategy()

```c
ArkUI_ErrorCode OH_ArkUI_TouchTestInfo_SetTouchResultStrategy(ArkUI_TouchTestInfo* info, ArkUI_TouchTestStrategy strategy);
```
**Description**

Sets the touch test policy, that is, the behavior of a component and its child components in a hit test. This API is applicable to scenarios where you want to customize the touch hit result, distribute touch events to a specified child component, or control whether sibling components continue to participate in the hit test.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TouchTestInfo](./capi-arkui-nativemodule-arkui-touchtestinfo.md)* info | Pointer to the touch test information.|
| [ArkUI_TouchTestStrategy](#arkui_touchteststrategy) strategy | Touch test policy. Select **ARKUI_TOUCH_TEST_STRATEGY_DEFAULT** if you do not need to customize the distribution and the system distributes events based on the hit status of the current node. Select **ARKUI_TOUCH_TEST_STRATEGY_FORWARD_COMPETITION** if you need to specify a child node to which the event is distributed and allow the system to determine whether to distribute the event to other sibling nodes. Select **ARKUI_TOUCH_TEST_STRATEGY_FORWARD** if you need to specify a child node to which the event is distributed and prohibit the event from being distributed to other sibling nodes. Select a policy based on whether you need to customize the distribution and whether sibling nodes are allowed to participate in the distribution. |

**Return value**

| Type| Description|
| -- | -- |
| ArkUI_ErrorCode | Result code.<br>Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.|

### OH_ArkUI_TouchTestInfo_SetTouchResultId()

```c
ArkUI_ErrorCode OH_ArkUI_TouchTestInfo_SetTouchResultId(ArkUI_TouchTestInfo* info, const char* id);
```
**Description**

Sets the ID of the child component that needs to be involved in the hit test. This API is applicable to scenarios where you want to customize the touch test result and distribute touch events to a specified child component.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TouchTestInfo](./capi-arkui-nativemodule-arkui-touchtestinfo.md)* info | Pointer to the touch test information.|
| const char* id | ID of a child component, which specifies the target child component involved in a hit test.|


**Return value**

| Type| Description|
| -- | -- |
| ArkUI_ErrorCode | Result code.<br>Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the input parameter is incorrect.|

### OH_ArkUI_DigitalCrownEvent_GetEventTime()

``` c
int64_t OH_ArkUI_DigitalCrownEvent_GetEventTime(const ArkUI_UIInputEvent* event)
```

**Description**

Obtains the time when a crown event occurs. The unit is ns. This API applies only when the input parameter **UIInputEvent** contains a crown event object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_UIInputEvent*](capi-arkui-eventmodule-arkui-uiinputevent.md) event | Pointer to the UI input event.|

**Return value**

| Type| Description|
| -- | -- |
| int64_t | Time when the UI input event occurs. If a parameter error occurs, **0** is returned.|

### OH_ArkUI_DigitalCrownEvent_GetAngularVelocity()

``` c
double OH_ArkUI_DigitalCrownEvent_GetAngularVelocity(const ArkUI_UIInputEvent* event)
```

**Description**

Obtains the angular velocity at which a crown event occurs. The unit is °/s. This API applies only when the input parameter **UIInputEvent** contains a crown event object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_UIInputEvent*](capi-arkui-eventmodule-arkui-uiinputevent.md) event | Pointer to the UI input event.|

**Return value**

| Type| Description|
| -- | -- |
| double | Angular velocity at which the UI input event occurs. If a parameter error occurs, **0.0** is returned.|

### OH_ArkUI_DigitalCrownEvent_GetDegree()

``` c
double OH_ArkUI_DigitalCrownEvent_GetDegree(const ArkUI_UIInputEvent* event)
```

**Description**

Obtains the rotation angle at which a crown event occurs. The unit is °. This API applies only when the input parameter **UIInputEvent** contains a crown event object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_UIInputEvent*](capi-arkui-eventmodule-arkui-uiinputevent.md) event | Pointer to the UI input event.|

**Return value**

| Type| Description|
| -- | -- |
| double | Rotation angle at which the UI input event occurs. If a parameter error occurs, **0.0** is returned.|

### OH_ArkUI_DigitalCrownEvent_GetAction()

``` c
ArkUI_CrownEvent_Action OH_ArkUI_DigitalCrownEvent_GetAction(const ArkUI_UIInputEvent* event)
```

**Description**

Obtains the phase at which a crown event occurs. This API applies only when the input parameter **UIInputEvent** contains a crown event object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_UIInputEvent*](capi-arkui-eventmodule-arkui-uiinputevent.md) event | Pointer to the UI input event.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_CrownEvent_Action](#arkui_crownevent_action)  | Action of rotating the crown when the UI input event occurs. If a parameter error occurs, [ARKUI_CROWNEVENT_ACTION_UNKNOWN](#arkui_crownevent_action) is returned.|

### OH_ArkUI_DigitalCrownEvent_SetStopPropagation()

``` c
ArkUI_ErrorCode OH_ArkUI_DigitalCrownEvent_SetStopPropagation(const ArkUI_UIInputEvent* event, bool stopPropagation)
```

**Description**

Sets whether to prevent event bubbling. This API is applicable when the current component has handled a crown event and does not want the event to be passed to its parent component or other ancestor components. This API applies only when the input parameter **UIInputEvent** contains a crown event object.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkUI_UIInputEvent*](capi-arkui-eventmodule-arkui-uiinputevent.md) event | Pointer to the UI input event.|
|bool stopPropagation|Whether to stop event propagation. The value **true** means to stop event propagation, and **false** means the opposite.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. The possible cause is that the event pointer, **pressedKeyCodes**, or **length** is invalid. Check the parameters and try again.<br>|
