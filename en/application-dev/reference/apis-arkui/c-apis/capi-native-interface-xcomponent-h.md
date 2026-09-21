# native_interface_xcomponent.h

## Overview

Declares APIs for accessing a Native XComponent.

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 8

**Related module**: [OH_NativeXComponent Native XComponent](capi-oh-nativexcomponent-native-xcomponent.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_NativeXComponent_HistoricalPoint](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent-historicalpoint.md) | OH_NativeXComponent_HistoricalPoint | Represents the historical point. |
| [OH_NativeXComponent_TouchPoint](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent-touchpoint.md) | OH_NativeXComponent_TouchPoint | Represents the touch point information of touch event. |
| [OH_NativeXComponent_TouchEvent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent-touchevent.md) | OH_NativeXComponent_TouchEvent | Represents the touch event. |
| [OH_NativeXComponent_MouseEvent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent-mouseevent.md) | OH_NativeXComponent_MouseEvent | Represents the mouse event information. |
| [OH_NativeXComponent_Callback](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent-callback.md) | OH_NativeXComponent_Callback | Registers the surface lifecycle and touch event callbacks. |
| [OH_NativeXComponent_MouseEvent_Callback](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent-mouseevent-callback.md) | OH_NativeXComponent_MouseEvent_Callback | Registers the mouse event callbacks. |
| [OH_NativeXComponent_ExpectedRateRange](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent-expectedraterange.md) | OH_NativeXComponent_ExpectedRateRange | Defines the expected frame rate range struct. |
| [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md) | OH_NativeXComponent | Provides an encapsulated <b>OH_NativeXComponent</b> instance. |
| [OH_NativeXComponent_KeyEvent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent-keyevent.md) | OH_NativeXComponent_KeyEvent | Provides an encapsulated <b>OH_NativeXComponent_KeyEvent</b> instance. |
| [OH_NativeXComponent_ExtraMouseEventInfo](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent-extramouseeventinfo.md) | OH_NativeXComponent_ExtraMouseEventInfo | Provides an encapsulated <b>OH_NativeXComponent_ExtraMouseEventInfo</b> instance which has extra info compared to OH_NativeXComponent_MouseEvent. |
| [OH_ArkUI_SurfaceHolder](capi-oh-nativexcomponent-native-xcomponent-oh-arkui-surfaceholder.md) | OH_ArkUI_SurfaceHolder | Provides an encapsulated <b>OH_ArkUI_SurfaceHolder</b> instance. |
| [OH_ArkUI_SurfaceCallback](capi-oh-nativexcomponent-native-xcomponent-oh-arkui-surfacecallback.md) | OH_ArkUI_SurfaceCallback | Define the surface lifecycle callback. |
| [NativeWindow](capi-oh-nativexcomponent-native-xcomponent-nativewindow.md) | OHNativeWindow | Forward declaration of OHNativeWindow. |
| [ArkUI_XComponentSurfaceConfig](capi-oh-nativexcomponent-native-xcomponent-arkui-xcomponentsurfaceconfig.md) | ArkUI_XComponentSurfaceConfig | Declares the config for Surface held by XComponent. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [anonymous0](#anonymous0) | - | Enumerates the API access states. |
| [ArkUI_XComponent_ImageAnalyzerState](#arkui_xcomponent_imageanalyzerstate) | ArkUI_XComponent_ImageAnalyzerState | Status code for AI analyzer. |
| [OH_NativeXComponent_TouchEventType](#oh_nativexcomponent_toucheventtype) | OH_NativeXComponent_TouchEventType | Represents the type of touch event. |
| [OH_NativeXComponent_TouchPointToolType](#oh_nativexcomponent_touchpointtooltype) | OH_NativeXComponent_TouchPointToolType | Represents the touch point tool type. |
| [OH_NativeXComponent_EventSourceType](#oh_nativexcomponent_eventsourcetype) | OH_NativeXComponent_EventSourceType | Represents the touch event source type. |
| [OH_NativeXComponent_MouseEventAction](#oh_nativexcomponent_mouseeventaction) | OH_NativeXComponent_MouseEventAction | Represents the mouse event action. |
| [OH_NativeXComponent_MouseEventButton](#oh_nativexcomponent_mouseeventbutton) | OH_NativeXComponent_MouseEventButton | Represents the mouse event button. |
| [OH_NativeXComponent_TouchEvent_SourceTool](#oh_nativexcomponent_touchevent_sourcetool) | OH_NativeXComponent_TouchEvent_SourceTool | Represents the source tool type of TouchEvent |

### Function

| Name | Description |
| -- | -- |
| [int32_t OH_NativeXComponent_GetXComponentId(OH_NativeXComponent* component, char* id, uint64_t* size)](#oh_nativexcomponent_getxcomponentid) | Obtains the ID of the ArkUI XComponent. |
| [int32_t OH_NativeXComponent_GetXComponentSize(OH_NativeXComponent* component, const void* window, uint64_t* width, uint64_t* height)](#oh_nativexcomponent_getxcomponentsize) | Obtains the size of the surface held by the ArkUI XComponent. |
| [int32_t OH_NativeXComponent_GetXComponentOffset(OH_NativeXComponent* component, const void* window, double* x, double* y)](#oh_nativexcomponent_getxcomponentoffset) | Obtains the offset of the surface held by the ArkUI XComponent. |
| [int32_t OH_NativeXComponent_GetTouchEvent(OH_NativeXComponent* component, const void* window, OH_NativeXComponent_TouchEvent* touchEvent)](#oh_nativexcomponent_gettouchevent) | Obtains the touch event dispatched by the ArkUI XComponent. |
| [int32_t OH_NativeXComponent_GetTouchPointToolType(OH_NativeXComponent* component, uint32_t pointIndex, OH_NativeXComponent_TouchPointToolType* toolType)](#oh_nativexcomponent_gettouchpointtooltype) | Obtains the touch pointer tool type by the ArkUI XComponent. |
| [int32_t OH_NativeXComponent_GetTouchPointTiltX(OH_NativeXComponent* component, uint32_t pointIndex, float* tiltX)](#oh_nativexcomponent_gettouchpointtiltx) | Obtains the touch pointer tiltX by the ArkUI XComponent. |
| [int32_t OH_NativeXComponent_GetTouchPointTiltY(OH_NativeXComponent* component, uint32_t pointIndex, float* tiltY)](#oh_nativexcomponent_gettouchpointtilty) | Obtains the touch pointer tiltX by the ArkUI XComponent. |
| [int32_t OH_NativeXComponent_GetTouchPointWindowX(OH_NativeXComponent* component, uint32_t pointIndex, float* windowX)](#oh_nativexcomponent_gettouchpointwindowx) | Obtains the x coordinate of a specific touch point relative to the upper left corner of the current application window from the ArkUI XComponent. |
| [int32_t OH_NativeXComponent_GetTouchPointWindowY(OH_NativeXComponent* component, uint32_t pointIndex, float* windowY)](#oh_nativexcomponent_gettouchpointwindowy) | Obtains the y coordinate of a specific touch point relative to the upper left corner of the current application window from the ArkUI XComponent. |
| [int32_t OH_NativeXComponent_GetTouchPointDisplayX(OH_NativeXComponent* component, uint32_t pointIndex, float* displayX)](#oh_nativexcomponent_gettouchpointdisplayx) | Obtains the x coordinate of a specific touch point relative to the upper left corner of the current screen from the ArkUI XComponent. |
| [int32_t OH_NativeXComponent_GetTouchPointDisplayY(OH_NativeXComponent* component, uint32_t pointIndex, float* displayY)](#oh_nativexcomponent_gettouchpointdisplayy) | Obtains the y coordinate of a specific touch point relative to the upper left corner of the current screen from the ArkUI XComponent. |
| [int32_t OH_NativeXComponent_GetHistoricalPoints(OH_NativeXComponent* component, const void* window, int32_t* size, OH_NativeXComponent_HistoricalPoint** historicalPoints)](#oh_nativexcomponent_gethistoricalpoints) | Obtains the touch event dispatched by the ArkUI XComponent. |
| [int32_t OH_NativeXComponent_GetMouseEvent(OH_NativeXComponent* component, const void* window, OH_NativeXComponent_MouseEvent* mouseEvent)](#oh_nativexcomponent_getmouseevent) | Obtains the mouse event dispatched by the ArkUI XComponent. |
| [int32_t OH_NativeXComponent_RegisterCallback(OH_NativeXComponent* component, OH_NativeXComponent_Callback* callback)](#oh_nativexcomponent_registercallback) | Registers a callback for this <b>OH_NativeXComponent</b> instance. |
| [int32_t OH_NativeXComponent_RegisterMouseEventCallback(OH_NativeXComponent* component, OH_NativeXComponent_MouseEvent_Callback* callback)](#oh_nativexcomponent_registermouseeventcallback) | Registers a callback for this <b>OH_NativeXComponent</b> instance. |
| [int32_t OH_NativeXComponent_GetExtraMouseEventInfo(OH_NativeXComponent* component, OH_NativeXComponent_ExtraMouseEventInfo** extraMouseEventInfo)](#oh_nativexcomponent_getextramouseeventinfo) | Obtains the extra mouse event dispatched by the ArkUI XComponent. |
| [int32_t OH_NativeXComponent_GetMouseEventModifierKeyStates(OH_NativeXComponent_ExtraMouseEventInfo* extraMouseEventInfo, uint64_t* keys)](#oh_nativexcomponent_getmouseeventmodifierkeystates) | Obtains the state of the modifier keys of the mouse event. |
| [int32_t OH_NativeXComponent_RegisterFocusEventCallback(OH_NativeXComponent* component, void (\*callback)(OH_NativeXComponent* component, void* window))](#oh_nativexcomponent_registerfocuseventcallback) | Registers a callback for this <b>OH_NativeXComponent</b> instance. |
| [int32_t OH_NativeXComponent_RegisterKeyEventCallback(OH_NativeXComponent* component, void (\*callback)(OH_NativeXComponent* component, void* window))](#oh_nativexcomponent_registerkeyeventcallback) | Registers a callback for this <b>OH_NativeXComponent</b> instance. |
| [int32_t OH_NativeXComponent_RegisterBlurEventCallback(OH_NativeXComponent* component, void (\*callback)(OH_NativeXComponent* component, void* window))](#oh_nativexcomponent_registerblureventcallback) | Registers a callback for this <b>OH_NativeXComponent</b> instance. |
| [int32_t OH_NativeXComponent_GetKeyEvent(OH_NativeXComponent* component, OH_NativeXComponent_KeyEvent** keyEvent)](#oh_nativexcomponent_getkeyevent) | Obtains the key event dispatched by the ArkUI XComponent. |
| [int32_t OH_NativeXComponent_GetKeyEventAction(OH_NativeXComponent_KeyEvent* keyEvent, OH_NativeXComponent_KeyAction* action)](#oh_nativexcomponent_getkeyeventaction) | Obtains the action of the key event. |
| [int32_t OH_NativeXComponent_GetKeyEventCode(OH_NativeXComponent_KeyEvent* keyEvent, OH_NativeXComponent_KeyCode* code)](#oh_nativexcomponent_getkeyeventcode) | Obtains the keyCode of the key event. |
| [int32_t OH_NativeXComponent_GetKeyEventSourceType(OH_NativeXComponent_KeyEvent* keyEvent, OH_NativeXComponent_EventSourceType* sourceType)](#oh_nativexcomponent_getkeyeventsourcetype) | Obtains the sourceType of the key event. |
| [int32_t OH_NativeXComponent_GetKeyEventDeviceId(OH_NativeXComponent_KeyEvent* keyEvent, int64_t* deviceId)](#oh_nativexcomponent_getkeyeventdeviceid) | Obtains the deviceId of the key event. |
| [int32_t OH_NativeXComponent_GetKeyEventTimestamp(OH_NativeXComponent_KeyEvent* keyEvent, int64_t* timestamp)](#oh_nativexcomponent_getkeyeventtimestamp) | Obtains the timestamp of the key event. |
| [int32_t OH_NativeXComponent_GetKeyEventModifierKeyStates(OH_NativeXComponent_KeyEvent* keyEvent, uint64_t* keys)](#oh_nativexcomponent_getkeyeventmodifierkeystates) | Obtains the state of the modifier keys of the key event. |
| [int32_t OH_NativeXComponent_GetKeyEventNumLockState(OH_NativeXComponent_KeyEvent* keyEvent, bool* isNumLockOn)](#oh_nativexcomponent_getkeyeventnumlockstate) | Obtains the Num Lock state of the key event. |
| [int32_t OH_NativeXComponent_GetKeyEventCapsLockState(OH_NativeXComponent_KeyEvent* keyEvent, bool* isCapsLockOn)](#oh_nativexcomponent_getkeyeventcapslockstate) | Obtains the Caps Lock state of the key event. |
| [int32_t OH_NativeXComponent_GetKeyEventScrollLockState(OH_NativeXComponent_KeyEvent* keyEvent, bool* isScrollLockOn)](#oh_nativexcomponent_getkeyeventscrolllockstate) | Obtains the Scroll Lock state of the key event. |
| [int32_t OH_NativeXComponent_SetExpectedFrameRateRange(OH_NativeXComponent* component, OH_NativeXComponent_ExpectedRateRange* range)](#oh_nativexcomponent_setexpectedframeraterange) | Set the Expected FrameRateRange. |
| [int32_t OH_NativeXComponent_RegisterOnFrameCallback(OH_NativeXComponent* component, void (\*callback)(OH_NativeXComponent* component, uint64_t timestamp, uint64_t targetTimestamp))](#oh_nativexcomponent_registeronframecallback) | Registers a callback for this <b>OH_NativeXComponent</b> instance. |
| [int32_t OH_NativeXComponent_UnregisterOnFrameCallback(OH_NativeXComponent* component)](#oh_nativexcomponent_unregisteronframecallback) | UnRegister a callback for this <b>OH_NativeXComponent</b> instance. |
| [int32_t OH_NativeXComponent_AttachNativeRootNode(OH_NativeXComponent* component, ArkUI_NodeHandle root)](#oh_nativexcomponent_attachnativerootnode) | Attaches the UI component created through the native API of ArkUI to this <b>OH_NativeXComponent</b> instance.(Deprecated in API20) |
| [int32_t OH_NativeXComponent_DetachNativeRootNode(OH_NativeXComponent* component, ArkUI_NodeHandle root)](#oh_nativexcomponent_detachnativerootnode) | Detaches the native component of ArkUI from this <b>OH_NativeXComponent</b> instance.(Deprecated in API20) |
| [int32_t OH_NativeXComponent_RegisterSurfaceShowCallback(OH_NativeXComponent* component, void (\*callback)(OH_NativeXComponent* component, void* window))](#oh_nativexcomponent_registersurfaceshowcallback) | Registers a callback for this <b>OH_NativeXComponent</b> instance. |
| [int32_t OH_NativeXComponent_RegisterSurfaceHideCallback(OH_NativeXComponent* component, void (\*callback)(OH_NativeXComponent* component, void* window))](#oh_nativexcomponent_registersurfacehidecallback) | Registers a callback for this <b>OH_NativeXComponent</b> instance. |
| [int32_t OH_NativeXComponent_RegisterUIInputEventCallback(OH_NativeXComponent* component, void (\*callback)(OH_NativeXComponent* component, ArkUI_UIInputEvent* event, ArkUI_UIInputEvent_Type type), ArkUI_UIInputEvent_Type type)](#oh_nativexcomponent_registeruiinputeventcallback) | Registers a UI input event callback for an <b>OH_NativeXComponent</b> instance and enables the callback to be invoked when a UI input event is received. Currently, only axis events are supported. |
| [int32_t OH_NativeXComponent_SetNeedSoftKeyboard(OH_NativeXComponent* component, bool needSoftKeyboard)](#oh_nativexcomponent_setneedsoftkeyboard) | Set whether the <b>OH_NativeXComponent</b> instance needs soft keyboard. |
| [int32_t OH_NativeXComponent_RegisterOnTouchInterceptCallback(OH_NativeXComponent* component, HitTestMode (\*callback)(OH_NativeXComponent* component, ArkUI_UIInputEvent* event))](#oh_nativexcomponent_registerontouchinterceptcallback) | Registers a custom event intercept callback for an <b>OH_NativeXComponent</b> instance. This enables the specified during hit testing. UI input-related operations are not supported on event objects received through this callback. For full functionality, use the <b>NODE_ON_TOUCH_INTERCEPT</b> event on native nodes instead. |
| [int32_t OH_NativeXComponent_GetTouchEventSourceType(OH_NativeXComponent* component, int32_t pointId, OH_NativeXComponent_EventSourceType* sourceType)](#oh_nativexcomponent_gettoucheventsourcetype) | Obtains the touch event's source type dispatched by the ArkUI XComponent. |
| [OH_NativeXComponent* OH_NativeXComponent_GetNativeXComponent(ArkUI_NodeHandle node)](#oh_nativexcomponent_getnativexcomponent) | Obtains the pointer to an <b>OH_NativeXComponent</b> instance based on the specified component instance created by the native API. |
| [int32_t OH_NativeXComponent_GetNativeAccessibilityProvider(OH_NativeXComponent* component, ArkUI_AccessibilityProvider** handle)](#oh_nativexcomponent_getnativeaccessibilityprovider) | Obtains the pointer to the <b> ArkUI_AccessibilityProvider</b> instance of this <b>OH_NativeXComponent</b> instance. |
| [int32_t OH_NativeXComponent_RegisterKeyEventCallbackWithResult(OH_NativeXComponent* component, bool (\*callback)(OH_NativeXComponent* component, void* window))](#oh_nativexcomponent_registerkeyeventcallbackwithresult) | Registers a callback for this <b>OH_NativeXComponent</b> instance. |
| [int32_t OH_ArkUI_XComponent_StartImageAnalyzer(ArkUI_NodeHandle node, void* userData, void (\*callback)(ArkUI_NodeHandle node, ArkUI_XComponent_ImageAnalyzerState statusCode, void* userData))](#oh_arkui_xcomponent_startimageanalyzer) | Start image analyzer for the specified XComponent instance created by the native API. |
| [int32_t OH_ArkUI_XComponent_StopImageAnalyzer(ArkUI_NodeHandle node)](#oh_arkui_xcomponent_stopimageanalyzer) | Stop image analyzer for the specified XComponent instance created by the native API. |
| [OH_ArkUI_SurfaceHolder* OH_ArkUI_SurfaceHolder_Create(ArkUI_NodeHandle node)](#oh_arkui_surfaceholder_create) | Create a <b>OH_ArkUI_SurfaceHolder</b> object from an XComponent node. |
| [void OH_ArkUI_SurfaceHolder_Dispose(OH_ArkUI_SurfaceHolder* surfaceHolder)](#oh_arkui_surfaceholder_dispose) | Disposes of a <b>OH_ArkUI_SurfaceHolder</b> object. |
| [int32_t OH_ArkUI_SurfaceHolder_SetUserData(OH_ArkUI_SurfaceHolder* surfaceHolder, void* userData)](#oh_arkui_surfaceholder_setuserdata) | Saves custom data on the <b>OH_ArkUI_SurfaceHolder</b> instance. |
| [void* OH_ArkUI_SurfaceHolder_GetUserData(OH_ArkUI_SurfaceHolder* surfaceHolder)](#oh_arkui_surfaceholder_getuserdata) | Obtains the custom data saved on the <b>OH_ArkUI_SurfaceHolder</b> instance. |
| [OH_ArkUI_SurfaceCallback* OH_ArkUI_SurfaceCallback_Create()](#oh_arkui_surfacecallback_create) | Create a <b>OH_ArkUI_SurfaceCallback</b> object. |
| [void OH_ArkUI_SurfaceCallback_Dispose(OH_ArkUI_SurfaceCallback* callback)](#oh_arkui_surfacecallback_dispose) | Disposes of a <b>OH_ArkUI_SurfaceCallback</b> object. |
| [void OH_ArkUI_SurfaceCallback_SetSurfaceCreatedEvent(OH_ArkUI_SurfaceCallback* callback, void (\*onSurfaceCreated)(OH_ArkUI_SurfaceHolder* surfaceHolder))](#oh_arkui_surfacecallback_setsurfacecreatedevent) | Set the surface created event of the surface callback. |
| [void OH_ArkUI_SurfaceCallback_SetSurfaceChangedEvent(OH_ArkUI_SurfaceCallback* callback, void (\*onSurfaceChanged)(OH_ArkUI_SurfaceHolder* surfaceHolder, uint64_t width, uint64_t height))](#oh_arkui_surfacecallback_setsurfacechangedevent) | Set the surface changed event of the surface callback. |
| [void OH_ArkUI_SurfaceCallback_SetSurfaceDestroyedEvent(OH_ArkUI_SurfaceCallback* callback, void (\*onSurfaceDestroyed)(OH_ArkUI_SurfaceHolder* surfaceHolder))](#oh_arkui_surfacecallback_setsurfacedestroyedevent) | Set the surface destroyed event of the surface callback. |
| [int32_t OH_ArkUI_SurfaceHolder_AddSurfaceCallback(OH_ArkUI_SurfaceHolder* surfaceHolder, OH_ArkUI_SurfaceCallback* callback)](#oh_arkui_surfaceholder_addsurfacecallback) | Adds a surface lifecycle callback for this <b>OH_ArkUI_SurfaceHolder</b> instance. |
| [int32_t OH_ArkUI_SurfaceHolder_RemoveSurfaceCallback(OH_ArkUI_SurfaceHolder* surfaceHolder, OH_ArkUI_SurfaceCallback* callback)](#oh_arkui_surfaceholder_removesurfacecallback) | Removes a previously added surface lifecycle callback from this <b>OH_ArkUI_SurfaceHolder</b> instance. |
| [OHNativeWindow* OH_ArkUI_XComponent_GetNativeWindow(OH_ArkUI_SurfaceHolder* surfaceHolder)](#oh_arkui_xcomponent_getnativewindow) | Obtains the nativeWindow associated with a <b>OH_ArkUI_SurfaceHolder</b> instance. |
| [int32_t OH_ArkUI_XComponent_SetAutoInitialize(ArkUI_NodeHandle node, bool autoInitialize)](#oh_arkui_xcomponent_setautoinitialize) | Set whether the XComponent node needs to initialize automatically. |
| [int32_t OH_ArkUI_XComponent_Initialize(ArkUI_NodeHandle node)](#oh_arkui_xcomponent_initialize) | Initialize the XComponent node. |
| [int32_t OH_ArkUI_XComponent_Finalize(ArkUI_NodeHandle node)](#oh_arkui_xcomponent_finalize) | Finalize the XComponent node. |
| [int32_t OH_ArkUI_XComponent_IsInitialized(ArkUI_NodeHandle node, bool* isInitialized)](#oh_arkui_xcomponent_isinitialized) | Obtains whether the XComponent node has initialized or not. |
| [int32_t OH_ArkUI_XComponent_SetExpectedFrameRateRange(ArkUI_NodeHandle node, OH_NativeXComponent_ExpectedRateRange range)](#oh_arkui_xcomponent_setexpectedframeraterange) | Set the Expected FrameRateRange for the XComponent node. |
| [int32_t OH_ArkUI_XComponent_RegisterOnFrameCallback(ArkUI_NodeHandle node, void (\*callback)(ArkUI_NodeHandle node, uint64_t timestamp, uint64_t targetTimestamp))](#oh_arkui_xcomponent_registeronframecallback) | Registers an onFrame callback for the XComponent node. |
| [int32_t OH_ArkUI_XComponent_UnregisterOnFrameCallback(ArkUI_NodeHandle node)](#oh_arkui_xcomponent_unregisteronframecallback) | UnRegister the onFrame callback for the XComponent node. |
| [int32_t OH_ArkUI_XComponent_SetNeedSoftKeyboard(ArkUI_NodeHandle node, bool needSoftKeyboard)](#oh_arkui_xcomponent_setneedsoftkeyboard) | Set whether the XComponent node needs soft keyboard when focused. |
| [ArkUI_AccessibilityProvider* OH_ArkUI_AccessibilityProvider_Create(ArkUI_NodeHandle node)](#oh_arkui_accessibilityprovider_create) | Create a <b>ArkUI_AccessibilityProvider</b> object from an XComponent node. |
| [void OH_ArkUI_AccessibilityProvider_Dispose(ArkUI_AccessibilityProvider* provider)](#oh_arkui_accessibilityprovider_dispose) | Disposes of an <b>ArkUI_AccessibilityProvider</b> object. |
| [void OH_ArkUI_SurfaceCallback_SetSurfaceShowEvent(OH_ArkUI_SurfaceCallback* callback, void (\*onSurfaceShow)(OH_ArkUI_SurfaceHolder* surfaceHolder))](#oh_arkui_surfacecallback_setsurfaceshowevent) | Set the surface show event of the surface callback. |
| [void OH_ArkUI_SurfaceCallback_SetSurfaceHideEvent(OH_ArkUI_SurfaceCallback* callback, void (\*onSurfaceHide)(OH_ArkUI_SurfaceHolder* surfaceHolder))](#oh_arkui_surfacecallback_setsurfacehideevent) | Set the surface hide event of the surface callback. |
| [ArkUI_XComponentSurfaceConfig* OH_ArkUI_XComponentSurfaceConfig_Create()](#oh_arkui_xcomponentsurfaceconfig_create) | Create an <b>ArkUI_XComponentSurfaceConfig</b> object. |
| [void OH_ArkUI_XComponentSurfaceConfig_Dispose(ArkUI_XComponentSurfaceConfig* config)](#oh_arkui_xcomponentsurfaceconfig_dispose) | Dispose of an <b>ArkUI_XComponentSurfaceConfig</b> object. |
| [void OH_ArkUI_XComponentSurfaceConfig_SetIsOpaque(ArkUI_XComponentSurfaceConfig* config, bool isOpaque)](#oh_arkui_xcomponentsurfaceconfig_setisopaque) | Set whether the surface held by XComponent needs to be considered opaque, even if the surface has translucent pixel. |
| [int32_t OH_ArkUI_SurfaceHolder_SetSurfaceConfig(OH_ArkUI_SurfaceHolder *surfaceHolder, ArkUI_XComponentSurfaceConfig *config)](#oh_arkui_surfaceholder_setsurfaceconfig) | Set surface config for this <b>OH_ArkUI_SurfaceHolder</b> instance. |

### Variable

| Name | Description |
| -- | -- |
| const uint32_t OH_XCOMPONENT_ID_LEN_MAX = 128 | Declares APIs for accessing a Native XComponent.<br>**Since**: 8<br>**System capability**: SystemCapability.ArkUI.ArkUI.Full |
| const uint32_t OH_MAX_TOUCH_POINTS_NUMBER = 10 |  |

## Enum type description

### anonymous0

```c
enum anonymous0
```

**Description**

Enumerates the API access states.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 8

| Enum item | Description |
| -- | -- |
| OH_NATIVEXCOMPONENT_RESULT_SUCCESS = 0 | Successful. |
| OH_NATIVEXCOMPONENT_RESULT_FAILED = -1 | Failed. |
| OH_NATIVEXCOMPONENT_RESULT_BAD_PARAMETER = -2 | Invalid parameters. |

### ArkUI_XComponent_ImageAnalyzerState

```c
enum ArkUI_XComponent_ImageAnalyzerState
```

**Description**

Status code for AI analyzer.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 18

| Enum item | Description |
| -- | -- |
| ARKUI_XCOMPONENT_AI_ANALYSIS_FINISHED = 0 | AI analyzer execution is finished. |
| ARKUI_XCOMPONENT_AI_ANALYSIS_DISABLED = 110000 | AI analyzer is disabled. |
| ARKUI_XCOMPONENT_AI_ANALYSIS_UNSUPPORTED = 110001 | AI analyzer is unsupported. |
| ARKUI_XCOMPONENT_AI_ANALYSIS_ONGOING = 110002 | AI analyzer is ongoing. |
| ARKUI_XCOMPONENT_AI_ANALYSIS_STOPPED = 110003 | AI analyzer is stopped. |

### OH_NativeXComponent_TouchEventType

```c
enum OH_NativeXComponent_TouchEventType
```

**Description**

Represents the type of touch event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 8

| Enum item | Description |
| -- | -- |
| OH_NATIVEXCOMPONENT_DOWN = 0 | Trigger a touch event when a finger is pressed. |
| OH_NATIVEXCOMPONENT_UP | Trigger a touch event when a finger is lifted. |
| OH_NATIVEXCOMPONENT_MOVE | Trigger a touch event when a finger moves on the screen in pressed state. |
| OH_NATIVEXCOMPONENT_CANCEL | Trigger an event when a touch event is canceled. |
| OH_NATIVEXCOMPONENT_UNKNOWN | Invalid touch type. |

### OH_NativeXComponent_TouchPointToolType

```c
enum OH_NativeXComponent_TouchPointToolType
```

**Description**

Represents the touch point tool type.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 9

| Enum item | Description |
| -- | -- |
| OH_NATIVEXCOMPONENT_TOOL_TYPE_UNKNOWN = 0 | Indicates invalid tool type. |
| OH_NATIVEXCOMPONENT_TOOL_TYPE_FINGER | Indicates a finger. |
| OH_NATIVEXCOMPONENT_TOOL_TYPE_PEN | Indicates a stylus. |
| OH_NATIVEXCOMPONENT_TOOL_TYPE_RUBBER | Indicates an eraser. |
| OH_NATIVEXCOMPONENT_TOOL_TYPE_BRUSH | Indicates a brush. |
| OH_NATIVEXCOMPONENT_TOOL_TYPE_PENCIL | Indicates a pencil. |
| OH_NATIVEXCOMPONENT_TOOL_TYPE_AIRBRUSH | Indicates a brush. |
| OH_NATIVEXCOMPONENT_TOOL_TYPE_MOUSE | Indicates a mouse. |
| OH_NATIVEXCOMPONENT_TOOL_TYPE_LENS | Indicates a lens. |

### OH_NativeXComponent_EventSourceType

```c
enum OH_NativeXComponent_EventSourceType
```

**Description**

Represents the touch event source type.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 9

| Enum item | Description |
| -- | -- |
| OH_NATIVEXCOMPONENT_SOURCE_TYPE_UNKNOWN = 0 | Indicates an unknown input source type. |
| OH_NATIVEXCOMPONENT_SOURCE_TYPE_MOUSE | Indicates that the input source generates a mouse multi-touch event. |
| OH_NATIVEXCOMPONENT_SOURCE_TYPE_TOUCHSCREEN | Indicates that the input source generates a touchscreen multi-touch event. |
| OH_NATIVEXCOMPONENT_SOURCE_TYPE_TOUCHPAD | Indicates that the input source generates a touchpad multi-touch event. |
| OH_NATIVEXCOMPONENT_SOURCE_TYPE_JOYSTICK | Indicates that the input source generates a joystick multi-touch event. |
| OH_NATIVEXCOMPONENT_SOURCE_TYPE_KEYBOARD | Indicates that the input source generates a keyboard event.<br>**Since**: 10 |

### OH_NativeXComponent_MouseEventAction

```c
enum OH_NativeXComponent_MouseEventAction
```

**Description**

Represents the mouse event action.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 9

| Enum item | Description |
| -- | -- |
| OH_NATIVEXCOMPONENT_MOUSE_CANCEL |  |

### OH_NativeXComponent_MouseEventButton

```c
enum OH_NativeXComponent_MouseEventButton
```

**Description**

Represents the mouse event button.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 9

| Enum item | Description |
| -- | -- |

### OH_NativeXComponent_TouchEvent_SourceTool

```c
enum OH_NativeXComponent_TouchEvent_SourceTool
```

**Description**

Represents the source tool type of TouchEvent

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 10

| Enum item | Description |
| -- | -- |


## Function description

### OH_NativeXComponent_GetXComponentId()

```c
int32_t OH_NativeXComponent_GetXComponentId(OH_NativeXComponent* component, char* id, uint64_t* size)
```

**Description**

Obtains the ID of the ArkUI XComponent.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md)* component | Indicates the pointer to this <b>OH_NativeXComponent</b> instance. |
| char* id | Indicates the char buffer to keep the ID of this <b>OH_NativeXComponent</b> instance. Notice that a null-terminator will be appended to the char buffer, so the size of the char buffer should be at least as large as the size of the real id length plus 1. It is recommended that the size of the char buffer be [OH_XCOMPONENT_ID_LEN_MAX + 1]. |
| uint64_t* size | Indicates the pointer to the length of <b>id</b>, which you can receive. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution. |

### OH_NativeXComponent_GetXComponentSize()

```c
int32_t OH_NativeXComponent_GetXComponentSize(OH_NativeXComponent* component, const void* window, uint64_t* width, uint64_t* height)
```

**Description**

Obtains the size of the surface held by the ArkUI XComponent.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md)* component | Indicates the pointer to this <b>OH_NativeXComponent</b> instance. |
| const void* window | Indicates the native window handler. |
| uint64_t* width | Indicates the pointer to the width of the current surface. |
| uint64_t* height | Indicates the pointer to the height of the current surface. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution. |

### OH_NativeXComponent_GetXComponentOffset()

```c
int32_t OH_NativeXComponent_GetXComponentOffset(OH_NativeXComponent* component, const void* window, double* x, double* y)
```

**Description**

Obtains the offset of the surface held by the ArkUI XComponent.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md)* component | Indicates the pointer to this <b>OH_NativeXComponent</b> instance. |
| const void* window | Indicates the native window handler. |
| double* x | Indicates the pointer to the x coordinate of the current surface. |
| double* y | Indicates the pointer to the y coordinate of the current surface. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution. |

### OH_NativeXComponent_GetTouchEvent()

```c
int32_t OH_NativeXComponent_GetTouchEvent(OH_NativeXComponent* component, const void* window, OH_NativeXComponent_TouchEvent* touchEvent)
```

**Description**

Obtains the touch event dispatched by the ArkUI XComponent.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md)* component | Indicates the pointer to this <b>OH_NativeXComponent</b> instance. |
| const void* window | Indicates the native window handler. |
| [OH_NativeXComponent_TouchEvent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent-touchevent.md)* touchEvent | Indicates the pointer to the current touch event. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution. |

### OH_NativeXComponent_GetTouchPointToolType()

```c
int32_t OH_NativeXComponent_GetTouchPointToolType(OH_NativeXComponent* component, uint32_t pointIndex, OH_NativeXComponent_TouchPointToolType* toolType)
```

**Description**

Obtains the touch pointer tool type by the ArkUI XComponent.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md)* component | Indicates the pointer to this <b>OH_NativeXComponent</b> instance. |
| uint32_t pointIndex | Indicates the pointer index in the touchPoints. |
| [OH_NativeXComponent_TouchPointToolType](capi-native-interface-xcomponent-h.md#oh_nativexcomponent_touchpointtooltype)* toolType | Indicates the tool Type of the pointer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution. |

### OH_NativeXComponent_GetTouchPointTiltX()

```c
int32_t OH_NativeXComponent_GetTouchPointTiltX(OH_NativeXComponent* component, uint32_t pointIndex, float* tiltX)
```

**Description**

Obtains the touch pointer tiltX by the ArkUI XComponent.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md)* component | Indicates the pointer to this <b>OH_NativeXComponent</b> instance. |
| uint32_t pointIndex | Indicates the pointer index in the touchPoints. |
| float* tiltX | Indicates the x tilt of the pointer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution. |

### OH_NativeXComponent_GetTouchPointTiltY()

```c
int32_t OH_NativeXComponent_GetTouchPointTiltY(OH_NativeXComponent* component, uint32_t pointIndex, float* tiltY)
```

**Description**

Obtains the touch pointer tiltX by the ArkUI XComponent.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md)* component | Indicates the pointer to this <b>OH_NativeXComponent</b> instance. |
| uint32_t pointIndex | Indicates the pointer index in the touchPoints. |
| float* tiltY | Indicates the y tilt of the pointer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution. |

### OH_NativeXComponent_GetTouchPointWindowX()

```c
int32_t OH_NativeXComponent_GetTouchPointWindowX(OH_NativeXComponent* component, uint32_t pointIndex, float* windowX)
```

**Description**

Obtains the x coordinate of a specific touch point relative to the upper left corner of the current application window from the ArkUI XComponent.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md)* component | Indicates the pointer to this <b>OH_NativeXComponent</b> instance. |
| uint32_t pointIndex | Indicates the pointer index in the touchPoints. |
| float* windowX | Indicates the x coordinate relative to the upper left corner of the current<br>          application window. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution.          [OH_NATIVEXCOMPONENT_RESULT_SUCCESS](capi-native-interface-xcomponent-h.md#anonymous0) get windowX success.          [OH_NATIVEXCOMPONENT_RESULT_BAD_PARAMETER](capi-native-interface-xcomponent-h.md#anonymous0) component is NULL, windowX is NULL\n          or native XComponent is NULL. |

### OH_NativeXComponent_GetTouchPointWindowY()

```c
int32_t OH_NativeXComponent_GetTouchPointWindowY(OH_NativeXComponent* component, uint32_t pointIndex, float* windowY)
```

**Description**

Obtains the y coordinate of a specific touch point relative to the upper left corner of the current application window from the ArkUI XComponent.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md)* component | Indicates the pointer to this <b>OH_NativeXComponent</b> instance. |
| uint32_t pointIndex | Indicates the pointer index in the touchPoints. |
| float* windowY | Indicates the y coordinate relative to the upper left corner of the current<br>          application window. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution.          [OH_NATIVEXCOMPONENT_RESULT_SUCCESS](capi-native-interface-xcomponent-h.md#anonymous0) get windowY success.          [OH_NATIVEXCOMPONENT_RESULT_BAD_PARAMETER](capi-native-interface-xcomponent-h.md#anonymous0) component is NULL, windowY is NULL\n          or native XComponent is NULL. |

### OH_NativeXComponent_GetTouchPointDisplayX()

```c
int32_t OH_NativeXComponent_GetTouchPointDisplayX(OH_NativeXComponent* component, uint32_t pointIndex, float* displayX)
```

**Description**

Obtains the x coordinate of a specific touch point relative to the upper left corner of the current screen from the ArkUI XComponent.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md)* component | Indicates the pointer to this <b>OH_NativeXComponent</b> instance. |
| uint32_t pointIndex | Indicates the pointer index in the touchPoints. |
| float* displayX | Indicates the x coordinate relative to the upper left corner of the current<br>          screen. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution.          [OH_NATIVEXCOMPONENT_RESULT_SUCCESS](capi-native-interface-xcomponent-h.md#anonymous0) get displayX success.          [OH_NATIVEXCOMPONENT_RESULT_BAD_PARAMETER](capi-native-interface-xcomponent-h.md#anonymous0) component is NULL, displayX is NULL\n          or native XComponent is NULL. |

### OH_NativeXComponent_GetTouchPointDisplayY()

```c
int32_t OH_NativeXComponent_GetTouchPointDisplayY(OH_NativeXComponent* component, uint32_t pointIndex, float* displayY)
```

**Description**

Obtains the y coordinate of a specific touch point relative to the upper left corner of the current screen from the ArkUI XComponent.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md)* component | Indicates the pointer to this <b>OH_NativeXComponent</b> instance. |
| uint32_t pointIndex | Indicates the pointer index in the touchPoints. |
| float* displayY | Indicates the y coordinate relative to the upper left corner of the current<br>          screen. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution.          [OH_NATIVEXCOMPONENT_RESULT_SUCCESS](capi-native-interface-xcomponent-h.md#anonymous0) get displayY success.          [OH_NATIVEXCOMPONENT_RESULT_BAD_PARAMETER](capi-native-interface-xcomponent-h.md#anonymous0) component is NULL, displayY is NULL\n          or native XComponent is NULL. |

### OH_NativeXComponent_GetHistoricalPoints()

```c
int32_t OH_NativeXComponent_GetHistoricalPoints(OH_NativeXComponent* component, const void* window, int32_t* size, OH_NativeXComponent_HistoricalPoint** historicalPoints)
```

**Description**

Obtains the touch event dispatched by the ArkUI XComponent.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md)* component | Indicates the pointer to this <b>OH_NativeXComponent</b> instance. |
| const void* window | Indicates the native window handler. |
| int32_t* size | Length of the historical touch point array. |
| [OH_NativeXComponent_HistoricalPoint](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent-historicalpoint.md)** historicalPoints | Pointer to the historical touch point array. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution. |

### OH_NativeXComponent_GetMouseEvent()

```c
int32_t OH_NativeXComponent_GetMouseEvent(OH_NativeXComponent* component, const void* window, OH_NativeXComponent_MouseEvent* mouseEvent)
```

**Description**

Obtains the mouse event dispatched by the ArkUI XComponent.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md)* component | Indicates the pointer to this <b>OH_NativeXComponent</b> instance. |
| const void* window | Indicates the native window handler. |
| [OH_NativeXComponent_MouseEvent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent-mouseevent.md)* mouseEvent | Indicates the pointer to the current mouse event. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution. |

### OH_NativeXComponent_RegisterCallback()

```c
int32_t OH_NativeXComponent_RegisterCallback(OH_NativeXComponent* component, OH_NativeXComponent_Callback* callback)
```

**Description**

Registers a callback for this <b>OH_NativeXComponent</b> instance.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md)* component | Indicates the pointer to this <b>OH_NativeXComponent</b> instance. |
| [OH_NativeXComponent_Callback](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent-callback.md)* callback | Indicates the pointer to a surface lifecycle and touch event callback. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution. |

### OH_NativeXComponent_RegisterMouseEventCallback()

```c
int32_t OH_NativeXComponent_RegisterMouseEventCallback(OH_NativeXComponent* component, OH_NativeXComponent_MouseEvent_Callback* callback)
```

**Description**

Registers a callback for this <b>OH_NativeXComponent</b> instance.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md)* component | Indicates the pointer to this <b>OH_NativeXComponent</b> instance. |
| [OH_NativeXComponent_MouseEvent_Callback](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent-mouseevent-callback.md)* callback | Indicates the pointer to a mouse event callback. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution. |

### OH_NativeXComponent_GetExtraMouseEventInfo()

```c
int32_t OH_NativeXComponent_GetExtraMouseEventInfo(OH_NativeXComponent* component, OH_NativeXComponent_ExtraMouseEventInfo** extraMouseEventInfo)
```

**Description**

Obtains the extra mouse event dispatched by the ArkUI XComponent.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md)* component | Indicates the pointer to this <b>OH_NativeXComponent</b> instance. |
| [OH_NativeXComponent_ExtraMouseEventInfo](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent-extramouseeventinfo.md)** extraMouseEventInfo | Indicates the pointer to pointer of <b>OH_NativeXComponent_ExtraMouseEventInfo</b> instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution.          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) the execution is successful.          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_NativeXComponent_GetMouseEventModifierKeyStates()

```c
int32_t OH_NativeXComponent_GetMouseEventModifierKeyStates(OH_NativeXComponent_ExtraMouseEventInfo* extraMouseEventInfo, uint64_t* keys)
```

**Description**

Obtains the state of the modifier keys of the mouse event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeXComponent_ExtraMouseEventInfo](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent-extramouseeventinfo.md)* extraMouseEventInfo | Indicates the pointer to this <b>OH_NativeXComponent_ExtraMouseEventInfo</b> instance. |
| uint64_t* keys | Pointer to a variable where the current combination of pressed modifier keys will be returned. The application can use bitwise operations to determine the state of each modifier key. Modifier keys can be referred to [ArkUI_ModifierKeyName](capi-ui-input-event-h.md#arkui_modifierkeyname). |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_NativeXComponent_RegisterFocusEventCallback()

```c
int32_t OH_NativeXComponent_RegisterFocusEventCallback(OH_NativeXComponent* component, void (*callback)(OH_NativeXComponent* component, void* window))
```

**Description**

Registers a callback for this <b>OH_NativeXComponent</b> instance.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| H_NativeXComponent\* component | Indicates the pointer to this <b>OH_NativeXComponent</b> instance. |
| void (\*callback)(OH_NativeXComponent\* component | Indicates the pointer to a focus event callback. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution. |

### OH_NativeXComponent_RegisterKeyEventCallback()

```c
int32_t OH_NativeXComponent_RegisterKeyEventCallback(OH_NativeXComponent* component, void (*callback)(OH_NativeXComponent* component, void* window))
```

**Description**

Registers a callback for this <b>OH_NativeXComponent</b> instance.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| H_NativeXComponent\* component | Indicates the pointer to this <b>OH_NativeXComponent</b> instance. |
| void (\*callback)(OH_NativeXComponent\* component | Indicates the pointer to a key event callback. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution. |

### OH_NativeXComponent_RegisterBlurEventCallback()

```c
int32_t OH_NativeXComponent_RegisterBlurEventCallback(OH_NativeXComponent* component, void (*callback)(OH_NativeXComponent* component, void* window))
```

**Description**

Registers a callback for this <b>OH_NativeXComponent</b> instance.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| H_NativeXComponent\* component | Indicates the pointer to this <b>OH_NativeXComponent</b> instance. |
| void (\*callback)(OH_NativeXComponent\* component | Indicates the pointer to a blur event callback. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution. |

### OH_NativeXComponent_GetKeyEvent()

```c
int32_t OH_NativeXComponent_GetKeyEvent(OH_NativeXComponent* component, OH_NativeXComponent_KeyEvent** keyEvent)
```

**Description**

Obtains the key event dispatched by the ArkUI XComponent.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md)* component | Indicates the pointer to this <b>OH_NativeXComponent</b> instance. |
| [OH_NativeXComponent_KeyEvent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent-keyevent.md)** keyEvent | Indicates the pointer to pointer of <b>OH_NativeXComponent_KeyEvent</b> instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution. |

### OH_NativeXComponent_GetKeyEventAction()

```c
int32_t OH_NativeXComponent_GetKeyEventAction(OH_NativeXComponent_KeyEvent* keyEvent, OH_NativeXComponent_KeyAction* action)
```

**Description**

Obtains the action of the key event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeXComponent_KeyEvent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent-keyevent.md)* keyEvent | Indicates the pointer to this <b>OH_NativeXComponent_KeyEvent</b> instance. |
| OH_NativeXComponent_KeyAction* action | Indicates the action of the <b>OH_NativeXComponent_KeyEvent</b> instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution. |

### OH_NativeXComponent_GetKeyEventCode()

```c
int32_t OH_NativeXComponent_GetKeyEventCode(OH_NativeXComponent_KeyEvent* keyEvent, OH_NativeXComponent_KeyCode* code)
```

**Description**

Obtains the keyCode of the key event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeXComponent_KeyEvent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent-keyevent.md)* keyEvent | Indicates the pointer to this <b>OH_NativeXComponent_KeyEvent</b> instance. |
| OH_NativeXComponent_KeyCode* code | Indicates the keyCode of the <b>OH_NativeXComponent_KeyEvent</b> instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution. |

### OH_NativeXComponent_GetKeyEventSourceType()

```c
int32_t OH_NativeXComponent_GetKeyEventSourceType(OH_NativeXComponent_KeyEvent* keyEvent, OH_NativeXComponent_EventSourceType* sourceType)
```

**Description**

Obtains the sourceType of the key event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeXComponent_KeyEvent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent-keyevent.md)* keyEvent | Indicates the pointer to this <b>OH_NativeXComponent_KeyEvent</b> instance. |
| [OH_NativeXComponent_EventSourceType](capi-native-interface-xcomponent-h.md#oh_nativexcomponent_eventsourcetype)* sourceType | Indicates the sourceType of the <b>OH_NativeXComponent_KeyEvent</b> instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution. |

### OH_NativeXComponent_GetKeyEventDeviceId()

```c
int32_t OH_NativeXComponent_GetKeyEventDeviceId(OH_NativeXComponent_KeyEvent* keyEvent, int64_t* deviceId)
```

**Description**

Obtains the deviceId of the key event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeXComponent_KeyEvent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent-keyevent.md)* keyEvent | Indicates the pointer to this <b>OH_NativeXComponent_KeyEvent</b> instance. |
| int64_t* deviceId | Indicates the deviceId of the <b>OH_NativeXComponent_KeyEvent</b> instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution. |

### OH_NativeXComponent_GetKeyEventTimestamp()

```c
int32_t OH_NativeXComponent_GetKeyEventTimestamp(OH_NativeXComponent_KeyEvent* keyEvent, int64_t* timestamp)
```

**Description**

Obtains the timestamp of the key event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeXComponent_KeyEvent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent-keyevent.md)* keyEvent | Indicates the pointer to this <b>OH_NativeXComponent_KeyEvent</b> instance. |
| int64_t* timestamp | Indicates the timestamp of the <b>OH_NativeXComponent_KeyEvent</b> instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution. |

### OH_NativeXComponent_GetKeyEventModifierKeyStates()

```c
int32_t OH_NativeXComponent_GetKeyEventModifierKeyStates(OH_NativeXComponent_KeyEvent* keyEvent, uint64_t* keys)
```

**Description**

Obtains the state of the modifier keys of the key event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeXComponent_KeyEvent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent-keyevent.md)* keyEvent | Indicates the pointer to this <b>OH_NativeXComponent_KeyEvent</b> instance. |
| uint64_t* keys | Pointer to a variable where the current combination of pressed modifier keys will be returned. The application can use bitwise operations to determine the state of each modifier key. Modifier keys can be referred to [ArkUI_ModifierKeyName](capi-ui-input-event-h.md#arkui_modifierkeyname). |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_NativeXComponent_GetKeyEventNumLockState()

```c
int32_t OH_NativeXComponent_GetKeyEventNumLockState(OH_NativeXComponent_KeyEvent* keyEvent, bool* isNumLockOn)
```

**Description**

Obtains the Num Lock state of the key event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeXComponent_KeyEvent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent-keyevent.md)* keyEvent | Indicates the pointer to this <b>OH_NativeXComponent_KeyEvent</b> instance. |
| bool* isNumLockOn | Return whether the Num Lock is on. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_NativeXComponent_GetKeyEventCapsLockState()

```c
int32_t OH_NativeXComponent_GetKeyEventCapsLockState(OH_NativeXComponent_KeyEvent* keyEvent, bool* isCapsLockOn)
```

**Description**

Obtains the Caps Lock state of the key event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeXComponent_KeyEvent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent-keyevent.md)* keyEvent | Indicates the pointer to this <b>OH_NativeXComponent_KeyEvent</b> instance. |
| bool* isCapsLockOn | Return whether the Caps Lock is on. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_NativeXComponent_GetKeyEventScrollLockState()

```c
int32_t OH_NativeXComponent_GetKeyEventScrollLockState(OH_NativeXComponent_KeyEvent* keyEvent, bool* isScrollLockOn)
```

**Description**

Obtains the Scroll Lock state of the key event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeXComponent_KeyEvent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent-keyevent.md)* keyEvent | Indicates the pointer to this <b>OH_NativeXComponent_KeyEvent</b> instance. |
| bool* isScrollLockOn | Return whether the Scroll Lock is on. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_NativeXComponent_SetExpectedFrameRateRange()

```c
int32_t OH_NativeXComponent_SetExpectedFrameRateRange(OH_NativeXComponent* component, OH_NativeXComponent_ExpectedRateRange* range)
```

**Description**

Set the Expected FrameRateRange.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md)* component | Indicates the pointer to this <b>OH_NativeXComponent</b> instance. |
| [OH_NativeXComponent_ExpectedRateRange](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent-expectedraterange.md)* range | Indicates the pointer to a expected rate range. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution. |

### OH_NativeXComponent_RegisterOnFrameCallback()

```c
int32_t OH_NativeXComponent_RegisterOnFrameCallback(OH_NativeXComponent* component, void (*callback)(OH_NativeXComponent* component, uint64_t timestamp, uint64_t targetTimestamp))
```

**Description**

Registers a callback for this <b>OH_NativeXComponent</b> instance.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| H_NativeXComponent\* component | Indicates the pointer to this <b>OH_NativeXComponent</b> instance. |
| void (\*callback)(OH_NativeXComponent\* component | Indicates the pointer to a onFrame callback. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution. |

### OH_NativeXComponent_UnregisterOnFrameCallback()

```c
int32_t OH_NativeXComponent_UnregisterOnFrameCallback(OH_NativeXComponent* component)
```

**Description**

UnRegister a callback for this <b>OH_NativeXComponent</b> instance.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md)* component | Indicates the pointer to this <b>OH_NativeXComponent</b> instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution. |

### OH_NativeXComponent_AttachNativeRootNode()

```c
int32_t OH_NativeXComponent_AttachNativeRootNode(OH_NativeXComponent* component, ArkUI_NodeHandle root)
```

**Description**

Attaches the UI component created through the native API of ArkUI to this <b>OH_NativeXComponent</b> instance.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Deprecated**: 20

**Replaced by**: OH_ArkUI_NodeContent_AddNode

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md)* component | Indicates the pointer to the <b>OH_NativeXComponent</b> instance. |
| ArkUI_NodeHandle root | Indicates the pointer to the component instance created by the native API. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns [OH_NATIVEXCOMPONENT_RESULT_SUCCESS](capi-native-interface-xcomponent-h.md#anonymous0) if the operation is successful.          Returns [OH_NATIVEXCOMPONENT_RESULT_BAD_PARAMETER](capi-native-interface-xcomponent-h.md#anonymous0) if a parameter error occurs. |

### OH_NativeXComponent_DetachNativeRootNode()

```c
int32_t OH_NativeXComponent_DetachNativeRootNode(OH_NativeXComponent* component, ArkUI_NodeHandle root)
```

**Description**

Detaches the native component of ArkUI from this <b>OH_NativeXComponent</b> instance.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Deprecated**: 20

**Replaced by**: OH_ArkUI_NodeContent_RemoveNode

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md)* component | Indicates the pointer to the <b>OH_NativeXComponent</b> instance. |
| ArkUI_NodeHandle root | Indicates the pointer to the component instance created by the native API. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns [OH_NATIVEXCOMPONENT_RESULT_SUCCESS](capi-native-interface-xcomponent-h.md#anonymous0) if the operation is successful.          Returns [OH_NATIVEXCOMPONENT_RESULT_BAD_PARAMETER](capi-native-interface-xcomponent-h.md#anonymous0) if a parameter error occurs. |

### OH_NativeXComponent_RegisterSurfaceShowCallback()

```c
int32_t OH_NativeXComponent_RegisterSurfaceShowCallback(OH_NativeXComponent* component, void (*callback)(OH_NativeXComponent* component, void* window))
```

**Description**

Registers a callback for this <b>OH_NativeXComponent</b> instance.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| H_NativeXComponent\* component | Indicates the pointer to this <b>OH_NativeXComponent</b> instance. |
| void (\*callback)(OH_NativeXComponent\* component | Indicates the pointer to a surface show event callback. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution. |

### OH_NativeXComponent_RegisterSurfaceHideCallback()

```c
int32_t OH_NativeXComponent_RegisterSurfaceHideCallback(OH_NativeXComponent* component, void (*callback)(OH_NativeXComponent* component, void* window))
```

**Description**

Registers a callback for this <b>OH_NativeXComponent</b> instance.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| H_NativeXComponent\* component | Indicates the pointer to this <b>OH_NativeXComponent</b> instance. |
| void (\*callback)(OH_NativeXComponent\* component | Indicates the pointer to a surface hide event callback. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution. |

### OH_NativeXComponent_RegisterUIInputEventCallback()

```c
int32_t OH_NativeXComponent_RegisterUIInputEventCallback(OH_NativeXComponent* component, void (*callback)(OH_NativeXComponent* component, ArkUI_UIInputEvent* event, ArkUI_UIInputEvent_Type type), ArkUI_UIInputEvent_Type type)
```

**Description**

Registers a UI input event callback for an <b>OH_NativeXComponent</b> instance and enables the callback to be invoked when a UI input event is received. Currently, only axis events are supported.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| H_NativeXComponent\* component | Indicates the pointer to the <b>OH_NativeXComponent</b> instance. |
| void (\*callback)(OH_NativeXComponent\* component | Indicates the pointer to the UI input event callback. |
| ArkUI_UIInputEvent_Type type) | Indicates the type of the current UI input event. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_NativeXComponent_SetNeedSoftKeyboard()

```c
int32_t OH_NativeXComponent_SetNeedSoftKeyboard(OH_NativeXComponent* component, bool needSoftKeyboard)
```

**Description**

Set whether the <b>OH_NativeXComponent</b> instance needs soft keyboard.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md)* component | Indicates the pointer to this <b>OH_NativeXComponent</b> instance. |
| bool needSoftKeyboard | Indicates whether the <b>OH_NativeXComponent</b> instance needs soft keyboard or not. Default value is false. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution. |

### OH_NativeXComponent_RegisterOnTouchInterceptCallback()

```c
int32_t OH_NativeXComponent_RegisterOnTouchInterceptCallback(OH_NativeXComponent* component, HitTestMode (*callback)(OH_NativeXComponent* component, ArkUI_UIInputEvent* event))
```

**Description**

Registers a custom event intercept callback for an <b>OH_NativeXComponent</b> instance. This enables the specified during hit testing. UI input-related operations are not supported on event objects received through this callback. For full functionality, use the <b>NODE_ON_TOUCH_INTERCEPT</b> event on native nodes instead.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| H_NativeXComponent\* component | Indicates the pointer to the <b>OH_NativeXComponent</b> instance. |
| HitTestMode (\*callback)(OH_NativeXComponent\* component | Indicates the pointer to the custom event intercept callback. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_NativeXComponent_GetTouchEventSourceType()

```c
int32_t OH_NativeXComponent_GetTouchEventSourceType(OH_NativeXComponent* component, int32_t pointId, OH_NativeXComponent_EventSourceType* sourceType)
```

**Description**

Obtains the touch event's source type dispatched by the ArkUI XComponent.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md)* component | Indicates the pointer to this <b>OH_NativeXComponent</b> instance. |
| int32_t pointId | Indicates the id of the touch point which triggers this touch event. |
| [OH_NativeXComponent_EventSourceType](capi-native-interface-xcomponent-h.md#oh_nativexcomponent_eventsourcetype)* sourceType | Indicates the source type of this touch event. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns OH_NATIVEXCOMPONENT_RESULT_SUCCESS if success.          Returns OH_NATIVEXCOMPONENT_RESULT_BAD_PARAMETER if a parameter exception occurs.          Returns OH_NATIVEXCOMPONENT_RESULT_FAILED if other exceptions occur. |

### OH_NativeXComponent_GetNativeXComponent()

```c
OH_NativeXComponent* OH_NativeXComponent_GetNativeXComponent(ArkUI_NodeHandle node)
```

**Description**

Obtains the pointer to an <b>OH_NativeXComponent</b> instance based on the specified component instance created by the native API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | Indicates the pointer to the component instance created by the native API. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_NativeXComponent*](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md) | Returns the pointer to the <b>OH_NativeXComponent</b> instance. |

### OH_NativeXComponent_GetNativeAccessibilityProvider()

```c
int32_t OH_NativeXComponent_GetNativeAccessibilityProvider(OH_NativeXComponent* component, ArkUI_AccessibilityProvider** handle)
```

**Description**

Obtains the pointer to the <b> ArkUI_AccessibilityProvider</b> instance of this <b>OH_NativeXComponent</b> instance.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md)* component | Indicates the pointer to the <b>OH_NativeXComponent</b> instance. |
| ArkUI_AccessibilityProvider** handle | Indicates the pointer to the <b>ArkUI_AccessibilityProvider</b> instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [OH_NATIVEXCOMPONENT_RESULT_SUCCESS](capi-native-interface-xcomponent-h.md#anonymous0) if the operation is successful.          Returns [OH_NATIVEXCOMPONENT_RESULT_BAD_PARAMETER](capi-native-interface-xcomponent-h.md#anonymous0) if a parameter error occurs. |

### OH_NativeXComponent_RegisterKeyEventCallbackWithResult()

```c
int32_t OH_NativeXComponent_RegisterKeyEventCallbackWithResult(OH_NativeXComponent* component, bool (*callback)(OH_NativeXComponent* component, void* window))
```

**Description**

Registers a callback for this <b>OH_NativeXComponent</b> instance.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| H_NativeXComponent\* component | Indicates the pointer to this <b>OH_NativeXComponent</b> instance. |
| bool (\*callback)(OH_NativeXComponent\* component | Indicates the pointer to a key event callback with result. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution.          [OH_NATIVEXCOMPONENT_RESULT_SUCCESS](capi-native-interface-xcomponent-h.md#anonymous0) the callback function is successfully registered.\n          [OH_NATIVEXCOMPONENT_RESULT_BAD_PARAMETER](capi-native-interface-xcomponent-h.md#anonymous0) component is nullptr or callback is nullptr.\n |

### OH_ArkUI_XComponent_StartImageAnalyzer()

```c
int32_t OH_ArkUI_XComponent_StartImageAnalyzer(ArkUI_NodeHandle node, void* userData, void (*callback)(ArkUI_NodeHandle node, ArkUI_XComponent_ImageAnalyzerState statusCode, void* userData))
```

**Description**

Start image analyzer for the specified XComponent instance created by the native API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_NodeHandle node | Indicates the pointer to the XComponent instance created by the native API. |
| void\* userData | Indicates the pointer to a user defined data. |
| void (\*callback)(ArkUI_NodeHandle node | Indicates the pointer to a image analyzer status callback function. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution.          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) the execution is successful.\n          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) component is nullptr or callback is nullptr,          or the type of node is not XComponent.\n |

### OH_ArkUI_XComponent_StopImageAnalyzer()

```c
int32_t OH_ArkUI_XComponent_StopImageAnalyzer(ArkUI_NodeHandle node)
```

**Description**

Stop image analyzer for the specified XComponent instance created by the native API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | Indicates the pointer to the XComponent instance created by the native API. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution.          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) the execution is successful.\n          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) component is nullptr or the type of node is not XComponent.\n |

### OH_ArkUI_SurfaceHolder_Create()

```c
OH_ArkUI_SurfaceHolder* OH_ArkUI_SurfaceHolder_Create(ArkUI_NodeHandle node)
```

**Description**

Create a <b>OH_ArkUI_SurfaceHolder</b> object from an XComponent node.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | Indicates the pointer to the XComponent node. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_ArkUI_SurfaceHolder*](capi-oh-nativexcomponent-native-xcomponent-oh-arkui-surfaceholder.md) | Returns the created <b>OH_ArkUI_SurfaceHolder</b> object's pointer. |

### OH_ArkUI_SurfaceHolder_Dispose()

```c
void OH_ArkUI_SurfaceHolder_Dispose(OH_ArkUI_SurfaceHolder* surfaceHolder)
```

**Description**

Disposes of a <b>OH_ArkUI_SurfaceHolder</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| node | Indicates the pointer to <b>OH_ArkUI_SurfaceHolder</b> object needed to dispose. |

### OH_ArkUI_SurfaceHolder_SetUserData()

```c
int32_t OH_ArkUI_SurfaceHolder_SetUserData(OH_ArkUI_SurfaceHolder* surfaceHolder, void* userData)
```

**Description**

Saves custom data on the <b>OH_ArkUI_SurfaceHolder</b> instance.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_SurfaceHolder](capi-oh-nativexcomponent-native-xcomponent-oh-arkui-surfaceholder.md)* surfaceHolder | Indicates the <b>OH_ArkUI_SurfaceHolder</b> instance on which the custom data will be saved. |
| void* userData | Indicates the custom data to be saved. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_SurfaceHolder_GetUserData()

```c
void* OH_ArkUI_SurfaceHolder_GetUserData(OH_ArkUI_SurfaceHolder* surfaceHolder)
```

**Description**

Obtains the custom data saved on the <b>OH_ArkUI_SurfaceHolder</b> instance.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_SurfaceHolder](capi-oh-nativexcomponent-native-xcomponent-oh-arkui-surfaceholder.md)* surfaceHolder | Indicates the target <b>OH_ArkUI_SurfaceHolder</b> instance. |

**Returns**:

| Type | Description |
| -- | -- |
| void* | Returns the custom data. |

### OH_ArkUI_SurfaceCallback_Create()

```c
OH_ArkUI_SurfaceCallback* OH_ArkUI_SurfaceCallback_Create()
```

**Description**

Create a <b>OH_ArkUI_SurfaceCallback</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Returns**:

| Type | Description |
| -- | -- |
| [OH_ArkUI_SurfaceCallback*](capi-oh-nativexcomponent-native-xcomponent-oh-arkui-surfacecallback.md) | Returns the created <b>OH_ArkUI_SurfaceCallback</b> object's pointer. |

### OH_ArkUI_SurfaceCallback_Dispose()

```c
void OH_ArkUI_SurfaceCallback_Dispose(OH_ArkUI_SurfaceCallback* callback)
```

**Description**

Disposes of a <b>OH_ArkUI_SurfaceCallback</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_SurfaceCallback](capi-oh-nativexcomponent-native-xcomponent-oh-arkui-surfacecallback.md)* callback | Indicates the pointer to <b>OH_ArkUI_SurfaceCallback</b> object needed to dispose. |

### OH_ArkUI_SurfaceCallback_SetSurfaceCreatedEvent()

```c
void OH_ArkUI_SurfaceCallback_SetSurfaceCreatedEvent(OH_ArkUI_SurfaceCallback* callback, void (*onSurfaceCreated)(OH_ArkUI_SurfaceHolder* surfaceHolder))
```

**Description**

Set the surface created event of the surface callback.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| H_ArkUI_SurfaceCallback\* callback | Indicated the pointer to the surface callback. |
| void (\*onSurfaceCreated)(OH_ArkUI_SurfaceHolder\* surfaceHolder) | Indicates the surface created callback event which will called when the surface is created. |

### OH_ArkUI_SurfaceCallback_SetSurfaceChangedEvent()

```c
void OH_ArkUI_SurfaceCallback_SetSurfaceChangedEvent(OH_ArkUI_SurfaceCallback* callback, void (*onSurfaceChanged)(OH_ArkUI_SurfaceHolder* surfaceHolder, uint64_t width, uint64_t height))
```

**Description**

Set the surface changed event of the surface callback.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| H_ArkUI_SurfaceCallback\* callback | Indicated the pointer to the surface callback. |
| void (\*onSurfaceChanged)(OH_ArkUI_SurfaceHolder\* surfaceHolder | Indicates the surface changed callback event which will called when the surface is changed. |

### OH_ArkUI_SurfaceCallback_SetSurfaceDestroyedEvent()

```c
void OH_ArkUI_SurfaceCallback_SetSurfaceDestroyedEvent(OH_ArkUI_SurfaceCallback* callback, void (*onSurfaceDestroyed)(OH_ArkUI_SurfaceHolder* surfaceHolder))
```

**Description**

Set the surface destroyed event of the surface callback.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| H_ArkUI_SurfaceCallback\* callback | Indicated the pointer to the surface callback. |
| void (\*onSurfaceDestroyed)(OH_ArkUI_SurfaceHolder\* surfaceHolder) | Indicates the surface destroyed callback event which will called when the surface is destroyed. |

### OH_ArkUI_SurfaceHolder_AddSurfaceCallback()

```c
int32_t OH_ArkUI_SurfaceHolder_AddSurfaceCallback(OH_ArkUI_SurfaceHolder* surfaceHolder, OH_ArkUI_SurfaceCallback* callback)
```

**Description**

Adds a surface lifecycle callback for this <b>OH_ArkUI_SurfaceHolder</b> instance.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_SurfaceHolder](capi-oh-nativexcomponent-native-xcomponent-oh-arkui-surfaceholder.md)* surfaceHolder | Indicates the pointer to this <b>OH_ArkUI_SurfaceHolder</b> instance. |
| [OH_ArkUI_SurfaceCallback](capi-oh-nativexcomponent-native-xcomponent-oh-arkui-surfacecallback.md)* callback | Indicates the pointer to this new callback. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution.          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) the execution is successful.          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_SurfaceHolder_RemoveSurfaceCallback()

```c
int32_t OH_ArkUI_SurfaceHolder_RemoveSurfaceCallback(OH_ArkUI_SurfaceHolder* surfaceHolder, OH_ArkUI_SurfaceCallback* callback)
```

**Description**

Removes a previously added surface lifecycle callback from this <b>OH_ArkUI_SurfaceHolder</b> instance.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_SurfaceHolder](capi-oh-nativexcomponent-native-xcomponent-oh-arkui-surfaceholder.md)* surfaceHolder | Indicates the pointer to this <b>OH_ArkUI_SurfaceHolder</b> instance. |
| [OH_ArkUI_SurfaceCallback](capi-oh-nativexcomponent-native-xcomponent-oh-arkui-surfacecallback.md)* callback | Indicates the pointer to the callback needed to remove. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution.          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) the execution is successful.          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_XComponent_GetNativeWindow()

```c
OHNativeWindow* OH_ArkUI_XComponent_GetNativeWindow(OH_ArkUI_SurfaceHolder* surfaceHolder)
```

**Description**

Obtains the nativeWindow associated with a <b>OH_ArkUI_SurfaceHolder</b> instance.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_SurfaceHolder](capi-oh-nativexcomponent-native-xcomponent-oh-arkui-surfaceholder.md)* surfaceHolder | Indicates the pointer to this <b>OH_ArkUI_SurfaceHolder</b> instance. |

**Returns**:

| Type | Description |
| -- | -- |
| [OHNativeWindow*](capi-oh-nativexcomponent-native-xcomponent-nativewindow.md) | Returns the nativeWindow associated with this <b>OH_ArkUI_SurfaceHolder</b> instance. |

### OH_ArkUI_XComponent_SetAutoInitialize()

```c
int32_t OH_ArkUI_XComponent_SetAutoInitialize(ArkUI_NodeHandle node, bool autoInitialize)
```

**Description**

Set whether the XComponent node needs to initialize automatically.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | Indicates the pointer to the XComponent node. |
| bool autoInitialize | Indicates whether the XComponent node needs to initialize automatically or not. If the value is true, OnSurfaceCreated will be called when the node is mounted and OnSurfaceDestroyed will be called when the node is unmounted. Default value is true. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution.          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) the execution is successful.          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the node is invalid. |

### OH_ArkUI_XComponent_Initialize()

```c
int32_t OH_ArkUI_XComponent_Initialize(ArkUI_NodeHandle node)
```

**Description**

Initialize the XComponent node.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | Indicates the pointer to the XComponent node. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution.          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) the execution is successful.          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the node is invalid.          [ARKUI_ERROR_CODE_XCOMPONENT_STATE_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the node has initialized. |

### OH_ArkUI_XComponent_Finalize()

```c
int32_t OH_ArkUI_XComponent_Finalize(ArkUI_NodeHandle node)
```

**Description**

Finalize the XComponent node.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | Indicates the pointer to the XComponent node. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution.          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) the execution is successful.          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the node is invalid.          [ARKUI_ERROR_CODE_XCOMPONENT_STATE_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the node has finalized. |

### OH_ArkUI_XComponent_IsInitialized()

```c
int32_t OH_ArkUI_XComponent_IsInitialized(ArkUI_NodeHandle node, bool* isInitialized)
```

**Description**

Obtains whether the XComponent node has initialized or not.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | Indicates the pointer to the XComponent node. |
| bool* isInitialized | Indicates whether the XComponent node has initialized. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution.          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) the execution is successful.          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the node is invalid. |

### OH_ArkUI_XComponent_SetExpectedFrameRateRange()

```c
int32_t OH_ArkUI_XComponent_SetExpectedFrameRateRange(ArkUI_NodeHandle node, OH_NativeXComponent_ExpectedRateRange range)
```

**Description**

Set the Expected FrameRateRange for the XComponent node.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | Indicates the pointer to the XComponent node. |
| [OH_NativeXComponent_ExpectedRateRange](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent-expectedraterange.md) range | Indicates the expected rate range. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution.          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) the execution is successful.          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_XComponent_RegisterOnFrameCallback()

```c
int32_t OH_ArkUI_XComponent_RegisterOnFrameCallback(ArkUI_NodeHandle node, void (*callback)(ArkUI_NodeHandle node, uint64_t timestamp, uint64_t targetTimestamp))
```

**Description**

Registers an onFrame callback for the XComponent node.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_NodeHandle node | Indicates the pointer to the XComponent node. |
| void (\*callback)(ArkUI_NodeHandle node | Indicates the pointer to an onFrame callback. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution.          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) the execution is successful.          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_XComponent_UnregisterOnFrameCallback()

```c
int32_t OH_ArkUI_XComponent_UnregisterOnFrameCallback(ArkUI_NodeHandle node)
```

**Description**

UnRegister the onFrame callback for the XComponent node.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | Indicates the pointer to the XComponent node. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution.          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) the execution is successful.          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_XComponent_SetNeedSoftKeyboard()

```c
int32_t OH_ArkUI_XComponent_SetNeedSoftKeyboard(ArkUI_NodeHandle node, bool needSoftKeyboard)
```

**Description**

Set whether the XComponent node needs soft keyboard when focused.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | Indicates the pointer to the XComponent node. |
| bool needSoftKeyboard | Indicates whether the XComponent node needs soft keyboard or not. Default value is false. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution.          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) the execution is successful.          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_AccessibilityProvider_Create()

```c
ArkUI_AccessibilityProvider* OH_ArkUI_AccessibilityProvider_Create(ArkUI_NodeHandle node)
```

**Description**

Create a <b>ArkUI_AccessibilityProvider</b> object from an XComponent node.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | Indicates the pointer to the XComponent node. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_AccessibilityProvider* | Returns the created <b>ArkUI_AccessibilityProvider</b> object's pointer. |

### OH_ArkUI_AccessibilityProvider_Dispose()

```c
void OH_ArkUI_AccessibilityProvider_Dispose(ArkUI_AccessibilityProvider* provider)
```

**Description**

Disposes of an <b>ArkUI_AccessibilityProvider</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_AccessibilityProvider* provider | Indicates the pointer to <b>ArkUI_AccessibilityProvider</b> object needed to dispose. |

### OH_ArkUI_SurfaceCallback_SetSurfaceShowEvent()

```c
void OH_ArkUI_SurfaceCallback_SetSurfaceShowEvent(OH_ArkUI_SurfaceCallback* callback, void (*onSurfaceShow)(OH_ArkUI_SurfaceHolder* surfaceHolder))
```

**Description**

Set the surface show event of the surface callback.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| H_ArkUI_SurfaceCallback\* callback | Indicated the pointer to the surface callback. |
| void (\*onSurfaceShow)(OH_ArkUI_SurfaceHolder\* surfaceHolder) | Indicates the surface show callback event which will called when the surface is shown. |

### OH_ArkUI_SurfaceCallback_SetSurfaceHideEvent()

```c
void OH_ArkUI_SurfaceCallback_SetSurfaceHideEvent(OH_ArkUI_SurfaceCallback* callback, void (*onSurfaceHide)(OH_ArkUI_SurfaceHolder* surfaceHolder))
```

**Description**

Set the surface hide event of the surface callback.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| H_ArkUI_SurfaceCallback\* callback | Indicated the pointer to the surface callback. |
| void (\*onSurfaceHide)(OH_ArkUI_SurfaceHolder\* surfaceHolder) | Indicates the surface hide callback event which will called when the surface is hide. |

### OH_ArkUI_XComponentSurfaceConfig_Create()

```c
ArkUI_XComponentSurfaceConfig* OH_ArkUI_XComponentSurfaceConfig_Create()
```

**Description**

Create an <b>ArkUI_XComponentSurfaceConfig</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_XComponentSurfaceConfig*](capi-oh-nativexcomponent-native-xcomponent-arkui-xcomponentsurfaceconfig.md) | A pointer to the object of the XComponent's surface config. |

### OH_ArkUI_XComponentSurfaceConfig_Dispose()

```c
void OH_ArkUI_XComponentSurfaceConfig_Dispose(ArkUI_XComponentSurfaceConfig* config)
```

**Description**

Dispose of an <b>ArkUI_XComponentSurfaceConfig</b> object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_XComponentSurfaceConfig](capi-oh-nativexcomponent-native-xcomponent-arkui-xcomponentsurfaceconfig.md)* config | A pointer to the object of the XComponent's surface config to be destroyed. |

### OH_ArkUI_XComponentSurfaceConfig_SetIsOpaque()

```c
void OH_ArkUI_XComponentSurfaceConfig_SetIsOpaque(ArkUI_XComponentSurfaceConfig* config, bool isOpaque)
```

**Description**

Set whether the surface held by XComponent needs to be considered opaque, even if the surface has translucent pixel.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_XComponentSurfaceConfig](capi-oh-nativexcomponent-native-xcomponent-arkui-xcomponentsurfaceconfig.md)* config | A pointer to the object of the XComponent's surface config. |
| bool isOpaque | Indicates whether the surface held by XComponent needs to be considered opaque, True means needing to be considered opaque, false otherwise. |

### OH_ArkUI_SurfaceHolder_SetSurfaceConfig()

```c
int32_t OH_ArkUI_SurfaceHolder_SetSurfaceConfig(OH_ArkUI_SurfaceHolder *surfaceHolder, ArkUI_XComponentSurfaceConfig *config)
```

**Description**

Set surface config for this <b>OH_ArkUI_SurfaceHolder</b> instance.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_SurfaceHolder](capi-oh-nativexcomponent-native-xcomponent-oh-arkui-surfaceholder.md) *surfaceHolder | Indicates the pointer to this <b>OH_ArkUI_SurfaceHolder</b> instance. |
| [ArkUI_XComponentSurfaceConfig](capi-oh-nativexcomponent-native-xcomponent-arkui-xcomponentsurfaceconfig.md) *config | Indicates the pointer to the XComponent's surface config. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution.          [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) the execution is successful.          [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |


